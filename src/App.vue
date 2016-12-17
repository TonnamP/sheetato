<template>
<div>
  <div id="app" v-show="App">
    <hello></hello>
    <button type="button" name="GoToRead" class="button button" @click="ChangePage(1)">Go To Read</button>
    <button type="button" name="UpLoad" class="button button" @click="ChangePage(2)">Upload</button>
  </div>
  <div v-show="gotoread" :change-page="ChangePage">
    <read-sheet :change-page="ChangePage" :sheets="sheets" :subjects="subjects"></read-sheet>
  </div>
  <div v-show="uploadsheet" :change-page="ChangePage">
    <upload-sheet :change-page="ChangePage" :up-file="upFile"></upload-sheet>
  </div>
</div>
</template>

<script>
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
var storageRef = storage.ref('sheets')
var Sheets = firebase.database().ref('sheets')
var Subjects = firebase.database().ref('subjects')
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
      str: '',
      sheets: [],
      subjects: []
    }
  },
  mounted () {
    var vm = this
    Sheets.on('child_added', function (data) {
      var item = data.val()
      item.id = data.key
      vm.sheets.push(item)
    })
    Sheets.on('child_removed', function (data) {
      var id = data.key
      var index = vm.sheets.findIndex(sheet => sheet.id === id)
      vm.sheets.splice(index, 1)
    })
    Subjects.on('child_added', function (data) {
      var item = data.val()
      item.id = data.key
      vm.subjects.push(item)
    })
    Subjects.on('child_removed', function (data) {
      var id = data.key
      var index = vm.subjects.findIndex(subject => subject.id === id)
      vm.subjects.splice(index, 1)
    })
  },
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
    upFile (file, subject, title) {
      var vm = this
      console.log('Uploading')
      storageRef.child(Date.now() + '/' + file.name).put(file).then(function (snapshot) {
        console.log(snapshot.downloadURL)
        console.log('Upload a base64 string')
        var data = {
          linkSheet: snapshot.downloadURL,
          subject: subject,
          title: title
        }
        // หาว่าเคยมีชื่อวิชานี้หรือยังถ้ายังไม่มีให้เพิ่มชื่อวิชานี้เข้าไป
        var index = vm.subjects.findIndex(s => s.name === subject)
        console.log(index)
        if (index === -1) {
          vm.addSubject(subject)
        }
        Sheets.push(data)
      })
    },
    addSubject (name) {
      Subjects.push({
        name: name
      })
    }
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
