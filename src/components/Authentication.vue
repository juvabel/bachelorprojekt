<template>
  <div class="uk-position-center uk-margin uk-margin-medium-top">
      <p class="uk-text-lead uk-text-large">Please look into the camera for authentication.<p/>
      <video id="video" width="560" height="340" autoplay muted></video>
  </div>
</template>

<script>
export default {
  name: 'Authentication',
  props: {
  },
  data: function () {
    return {
      currentComponent: 'Authentication'
    }
  },
  methods: {
    // send new component to App.vue to change it
    newCurrentComponent: function () {
      this.$emit('newComponent', 'Identification')
    },
    startVideo: async function () {
      const video = document.getElementById('video')
      navigator.getUserMedia(
        { video: {} },
        stream => { video.srcObject = stream },
        err => console.error(err)
      )
      video.addEventListener('play', async () => {
        const LabeledFaceDescriptors = await this.loadLabeledImages()
        const faceMatcher = new window.faceapi.FaceMatcher(LabeledFaceDescriptors, 0.6)
        const canvas2 = window.faceapi.createCanvasFromMedia(video)
        document.body.append(canvas2)
        const displaySize = { width: video.width, height: video.height }
        window.faceapi.matchDimensions(canvas2, displaySize)
        setInterval(async () => {
          // const detections = await window.faceapi.detectAllFaces(video,
          // new window.faceapi.TinyFaceDetectorOptions()).withFaceLandmarks().withFaceDescriptors()
          const detections = await window.faceapi.detectAllFaces(video).withFaceLandmarks().withFaceDescriptors()
          console.log(detections)
          const resizedDetections = window.faceapi.resizeResults(detections, displaySize)
          const results = resizedDetections.map(d => faceMatcher.findBestMatch(d.descriptor))
          console.log(results)
          results.forEach((result, i) => {
            const box = resizedDetections[i].detection.box
            const drawBox = new window.faceapi.draw.DrawBox(box, { label: result.toString() })
            drawBox.draw(canvas2)
          })
          canvas2.getContext('2d').clearRect(0, 0, canvas2.width, canvas2.height)
          window.faceapi.draw.drawDetections(canvas2, resizedDetections)
        }, 100)
      })
      setTimeout(this.newCurrentComponent, 3000)
    },
    loadLabeledImages: function () {
      const labels = ['Julia']
      return Promise.all(
        labels.map(async label => {
          const descriptions = []
          for (let i = 1; i <= 2; i++) {
            const img = await window.faceapi.fetchImage(`/users_images/${label}/${i}.JPG`)
            const detections = await window.faceapi.detectSingleFace(img).withFaceLandmarks().withFaceDescriptor()
            descriptions.push(detections.descriptor)
          }
          return new window.faceapi.LabeledFaceDescriptor(label, descriptions)
        })
      )
    }
  },
  mounted () {
    Promise.all([
      window.faceapi.nets.tinyFaceDetector.loadFromUri('/models'),
      window.faceapi.nets.faceLandmark68Net.loadFromUri('/models'),
      window.faceapi.nets.faceRecognitionNet.loadFromUri('/models'),
      window.faceapi.nets.ssdMobilenetv1.loadFromUri('/models')
    ]).then(this.startVideo())
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="less">
canvas {
    position: absolute;
}

</style>
