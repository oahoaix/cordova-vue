<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <button @click="takePicture()">take picture</button>
    <image :src="url"></image>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  data () {
    return {
      msg: 'Welcome to Your Vue.js App',
      url: null,
    }
  },
  methods:{
    takePicture(){
      var that = this
      navigator.camera.getPicture(onSuccess, onFail, {
        quality: 50,
        destinationType: Camera.DestinationType.DATA_URL
      })

      function onSuccess(imageData){
        that.url = "data:image/jpeg;base64," + imageData
      }

      function onFail(message){
        alert(message)
      }
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
