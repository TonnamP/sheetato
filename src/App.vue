<template>
  <div>
<div id="app" v-show="App">
  <hello></hello>
  <button type="button" name="GoToRead" class="button button" @click="ChangePage(1)">Go To Read</button>
  <button type="button" name="UpLoad" class="button button" @click="ChangePage(2)">Upload</button>
</div>
<div v-show="gotoread" :change-page="ChangePage">
  <read-sheet :change-page="ChangePage"></read-sheet>
</div>
<div v-show="uploadsheet" :change-page="ChangePage">
  <upload-sheet :change-page="ChangePage"></upload-sheet>
</div>
</div>
</template>

<script>
import Hello from './components/Hello'
import ReadSheet from './components/ReadSheet'
import UploadSheet from './components/UploadSheet'
export default {
  name: 'app',
  data () {
    return {
      gotoread: false,
      uploadsheet: false,
      App: true
    }
  },
  components: {
    Hello,
    ReadSheet,
    UploadSheet
  },
  methods: {
    ChangePage (page) {
      console.log(page)
      if (page === 1) {
        this.gotoread = true
        this.App = false
        this.uploadsheet = false
      } if (page === 2) {
        this.uploadsheet = true
        this.gotoread = false
        this.App = false
      } if (page === 3) {
        this.uploadsheet = false
        this.gotoread = false
        this.App = false
      }
    }
  }
}
</script>
<style>
@import url('https://fonts.googleapis.com/css?family=Raleway');

body {
  font-family: 'Raleway', sans-serif;
}

#app {
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 270px;
}

.button {
  background-color: #000000;
  /* Green */
  border: none;
  border-radius: 8px;
  color: white;
  padding: 16px 32px;
  text-align: center;
  text-decoration: none;
  display: inline-block;
  font-size: 16px;
  margin: 4px 2px;
  -webkit-transition-duration: 0.4s;
  /* Safari */
  transition-duration: 0.4s;
  cursor: pointer;
  width: 200px;
  height: 50px;
}
</style>
