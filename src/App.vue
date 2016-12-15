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
    <upload-sheet :change-page="ChangePage" :create-p-d-f="createPDF" :up-file="upFile"></upload-sheet>
  </div>
</div>
</template>

<script>
// Initialize Firebase
/* global FileReader, btoa */
import firebase from 'firebase'
var config = {
  apiKey: 'AIzaSyCq9l98zJYY7iDJG0dWphAOULQEf39lmwM',
  authDomain: 'sheetato.firebaseapp.com',
  databaseURL: 'https://sheetato.firebaseio.com',
  storageBucket: 'sheetato.appspot.com',
  messagingSenderId: '196311840371'
}
firebase.initializeApp(config)
var storage = firebase.storage()
var storageRef = storage.ref()
var ref = storageRef.child('images')
import Hello from './components/Hello'
import ReadSheet from './components/ReadSheet'
import UploadSheet from './components/UploadSheet'
export default {
  name: 'app',
  data () {
    return {
      gotoread: false,
      uploadsheet: false,
      App: true,
      str: ''
    }
  },
  /* endData */
  components: {
    Hello,
    ReadSheet,
    UploadSheet
  },
  /* endCompponents */
  methods: {
    ChangePage (page) {
      if (page === 1) {
        this.gotoread = true
        this.App = false
        this.uploadsheet = false
      }
      if (page === 2) {
        this.uploadsheet = true
        this.gotoread = false
        this.App = false
      }
      if (page === 3) {
        this.uploadsheet = false
        this.gotoread = false
        this.App = false
      }
    },
    /* endChangePage */
    UploadFile () {
      var message = this.str
      ref.putString(message, 'base64').then(function (snapshot) {
        console.log(snapshot)
      })
    },
    /* endUploadFile */
    createPDF (f) {
      var vm = this
      var files = f.target.files
      var file = files[0]
      var reader = new FileReader()
      reader.onload = (e) => {
        vm.str = e.target.result
        console.log(vm.str)
        console.log('test')
        vm.str = btoa(vm.str)
        console.log(vm.str)
      }
      reader.readAsDataURL(file)
    },
    /* endcreatePDF */
    upFile () {
      console.log('Upload')
      var vm = this
      var message = vm.str
      ref.putString(message, 'base64').then(function (snapshot) {
        console.log(snapshot)
        console.log('Uploaded a base64 string!')
      })
    }
    /* endupFile */
  }
  /* endMethods */
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
