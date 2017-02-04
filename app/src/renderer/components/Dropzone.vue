<template>
  <div>
    <div>
      <div
        :class="['dropzone-area', dragging ? 'dropzone-over' : '']"
        drag-over="handleDragOver"
        @dragenter="dragging=true"
        @dragleave="dragging=false">

          <div class="dropzone-text">
              <img src="./assets/electracity.png" />
              <span class="dropzone-title">Click to open, or drop your audio files here</span>
          </div>
          <input type="file" @change="onFileChange">
      </div>
  </div>
</div>
</template>

<script>
export default {
  props: ['help'],
  name: 'dropzone',
  data() {
      return {
          dragging: false
      }
  },

  methods: {
      onFileChange(e) {
          var files = e.target.files || e.dataTransfer.files;
          if (!files.length) return;
      },
  }
}
</script>
<style>
.dropzone-over {

  border: 1px solid red !important;
}

.dropzone-area {
    margin-top: 2em;
    width: 100%;
    height: 400px;
    position: relative;
    border: 2px dashed #CBCBCB;
    &:hover {
        border: 2px dashed #2E94C4;
        .dropzone-title {
          color: #1975A0;
        }

    }
}

.dropzone-area input {
    position: absolute;
    cursor: pointer;
    top: 0px;
    right: 0;
    bottom: 0;
    left: 0;
    width: 100%;
    height: 100%;
    opacity: 0;
}

.dropzone-text {
    position: absolute;
    top: 50%;
    text-align: center;
    transform: translate(0, -50%);
    width: 100%;
    span {
        display: block;
        font-family: Arial, Helvetica;
        line-height: 1.9;
    }
}

.dropzone-title {
    font-size: 13px;
    color: #787878;
    letter-spacing: 0.4px;
}
.dropzone-info {
    font-size: 13px;
    font-size: 0.8125rem;
    color: #A8A8A8;
    letter-spacing: 0.4px;
}

.dropzone-button {
    position: absolute;
    top: 10px;
    right: 10px;
    display: none;
}

.dropzone-preview {
    width: 80%;
    position: relative;
    &:hover .dropzone-button {
        display: block;
    }
    img {
      display: block;
      height: auto;
      max-width: 100%;
    }

}
</style>
