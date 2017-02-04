<template>
  <div>
  <div class="tabs is-right">
    <ul>
        <input type="file" id='input' @change="addfile" multiple>
    </ul>
  </div>
  <div class="container">
    <div v-if="data.length > 0">
      <player :urls="data"></player>
     </div>
  </div>
  </div>
</template>

<script>
  import Player from './Player.vue'
  import fontawesome from 'font-awesome/css/font-awesome.min.css'
  import fs from 'fs'

  export default {
    components: {
      Player
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
      addfile(e) {

        var trackstoload = []

        for (let s of e.target.files) {
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
  img {
    margin-top: -25px;
    width: 450px;
  }

  #input {
    margin-top: 10px;
    margin-bottom: 10px;
  }
</style>
