<template>
<div class="bgcolor">
  <ul>
    <li><a class="active">Upload Sheet</a></li>
    <li><a @click="ChangePage(1)" class="active1">Read</a></li>
  </ul>
  <div class="form-style-6">
    <h1>Upload File</h1>
      <input type="text" name="subject" placeholder="Subject" class="subject" v-model="subject" />
      <input type="text" name="title" placeholder="Title" class="subject" v-model="title"/>
      <input type="file" name="choosfile" placeholder="Choose File" class="choose" accept="application/pdf" v-on:change="selectFile">
      <button class="canup1" @click="up">Upload</button> <button value="Cancle" class="canup2">Cancle</button>
  </div>
</div>
</template>

<script>
export default {
  props: ['ChangePage', 'upFile', 'sheets'],
  name: 'upload',
  data () {
    return {
      file: '',
      subject: '',
      title: ''
    }
  },
  methods: {
    selectFile (e) {
      var files = e.target.files
      this.file = files[0]
    },
    up () {
      this.upFile(this.file, this.subject, this.title)
      this.file = ''
      this.subject = ''
      this.title = ''
    }
  }
}
</script>

<style scoped>
@import url('https://fonts.googleapis.com/css?family=Raleway');
ul {
  -webkit-box-sizing: border-box;
  -moz-box-sizing: border-box;
  box-sizing: border-box;
  list-style-type: none;
  margin: 0;
  padding: 0;
  overflow: hidden;
  background-color: #333;
}

li {
  float: left;
}

li a {
  -webkit-box-sizing: border-box;
  -moz-box-sizing: border-box;
  box-sizing: border-box;
  display: block;
  color: white;
  text-align: center;
  padding: 14px 16px;
  text-decoration: none;
}

li a:hover {
  background-color: #000000;
  color: #ffffff;
}

.active1 {
  background-color: #333;
  margin-left: 1200px;
  font-size: 18;
}

.active {
  margin-top: 5px;
  font-size: 10px;
  background-color: #333;
}

h1,
h2 {
  font-weight: normal;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  display: inline-block;
  margin: 0 10px;
}

a {
  color: #42b983;
}

.search {
  border-radius: 8px;
  width: 300px;
  height: 30px;
  margin-top: 8px;
  margin-left: 750px;
  background-image: url('http://www.bicycling.com/sites/all/themes/zeus_base/images/svg/search.svg');
  background-position: 3px 5px;
  background-repeat: no-repeat;
  background-size: 20px;
  padding-left: 30px;
}

.form-style-6 {
  font-family: 'Raleway', sans-serif;
  max-width: 500px;
  height: 320px;
  margin: 10px auto;
  margin-top: 100px;
  padding: 20px;
  background: #F7F7F7;
}

.form-style-6 h1 {
  background: #000000;
  padding: 20px 0;
  font-size: 140%;
  font-weight: 300;
  text-align: center;
  color: #fff;
  margin: -16px -16px 16px -16px;
}

.subject {
  -webkit-transition: all 0.30s ease-in-out;
  -moz-transition: all 0.30s ease-in-out;
  -ms-transition: all 0.30s ease-in-out;
  -o-transition: all 0.30s ease-in-out;
  outline: none;
  box-sizing: border-box;
  -webkit-box-sizing: border-box;
  -moz-box-sizing: border-box;
  width: 100%;
  background: #fff;
  margin-bottom: 4%;
  border: 1px solid #ccc;
  padding: 3%;
  color: #555;
  font: 95% 'Raleway', Helvetica, sans-serif;
}

.subject input[type="text"]:focus,
.subject select:focus {
  padding: 3%;
  border: 1px solid #000000;
}

.choose {
  -webkit-transition: all 0.30s ease-in-out;
  -moz-transition: all 0.30s ease-in-out;
  -ms-transition: all 0.30s ease-in-out;
  -o-transition: all 0.30s ease-in-out;
  outline: none;
  box-sizing: border-box;
  -webkit-box-sizing: border-box;
  -moz-box-sizing: border-box;
  width: 100%;
  background: #fff;
  margin-bottom: 4%;
  border: 1px solid #ccc;
  padding: 3%;
  color: #555;
  font: 95% 'Raleway', Helvetica, sans-serif;
}

.choose input[type="text"]:focus,
.choose select:focus {
  padding: 3%;
  border: 1px solid #000000;
}

.choosefile {
  width: 30%;
  padding: 3%;
  background: #000000;
  margin-bottom: 5px;
  color: #ffffff;
  font-family: 50% 'Raleway', sans-serif;
  display: inline-block;
}

.choosefile:hover,
.choosefile:hover {
  background: #ffffff;
  color: #000000;
}

.canup1 {
  width: 45%;
  padding: 3%;
  background: #000000;
  margin-bottom: 5px;
  margin-left: 20px;
  color: #ffffff;
  font-family: 'Raleway', sans-serif;
  font-size: 100%;
  display: inline-block;
}
.canup1:hover,
.canup1:hover {
  background: #ffffff;
  color: #000000;
}
.canup2 {
  width: 45%;
  padding: 3%;
  background: #000000;
  margin-bottom: 5px;
  margin-left: 0px;
  color: #ffffff;
  font-family: 'Raleway', sans-serif;
  font-size: 100%;
  display: inline-block;
}
.canup2:hover,
.canup2:hover {
  background: #ffffff;
  color: #000000;
}
.bgcolor {
  background-color: #ffffff;
  width: 100vu;
  height: 100vh;
}

.choose input[type='file'] {
  width: 30%;
  padding: 3%;
  background: #000000;
  margin-bottom: 5px;
  color: #ffffff;
  font-family: 'Raleway', sans-serif;
  display: inline-block;
}
</style>
