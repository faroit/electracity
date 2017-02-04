<template>
  <div class="container">
  <dropzone v-if="data.length == 0" v-on:addfiles="addfiles"></dropzone>
  <div class="container">
    <div v-if="data.length > 0">
      <player :urls="data"></player>
    </div>
  </div>
  </div>
</template>

<script>
  import Player from './Player.vue'
  import Dropzone from './Dropzone.vue'
  import fontawesome from 'font-awesome/css/font-awesome.min.css'

  export default {
    components: {
      Player, Dropzone
    },
    data: function () {
      return {
        data: [],
      }
    },
    name: 'landing-page',
    methods: {
      showSuccess: function (file) {
        console.log('A file was successfully uploaded')
      },
      addfiles: function(e) {
        var trackstoload = []

        for (let s of e) {
          console.log(s)
          trackstoload.push(
            {
              'name': s.name,
              'customClass': 'mix',
              'solo': false,
              'mute': false,
              'file': s.path
            }
          )
        }

        this.data = trackstoload;
      }
    }
  }
</script>

<style scoped>
  body {
    margin:0;
  }
  img {
    margin-top: -25px;
    width: 450px;
  }

  #input {
    margin-top: 10px;
    margin-bottom: 10px;
  }

  #logo {
    margin-left: 30em;
    margin-top: 10em;
    text-align: center;
  }
</style>
