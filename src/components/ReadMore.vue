<template>
<div class="bgcolor">
  <div class="" v-for="sheet in sheets" v-if="sheet.subject === selectSubject" class="form-style-6">
    <h1>{{sheet.title}}</h1>
    <h3><a target="_blank" :href="sheet.linkSheet">Click to read sheet</a></h3>
  </div>
  <div>
    <button type="submit" name="button" align="center" @click="setRead(0)" class="button">Back</button>
    <read-sheet v-if="read === 0"></read-sheet>
</div>
</template>

<script>
import ReadSheet from './ReadSheet'
export default {
  props: ['sheets', 'selectSubject', 'ChangePage', 'read', 'setRead'],
  data () {
    return {
    }
  },
  methods: {},
  components: {
    ReadSheet
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
  background-color: #F8F8FF;
  color: #000000;
}

.active {
  -webkit-box-sizing: border-box;
  -moz-box-sizing: border-box;
  box-sizing: border-box;
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
.center {
  font-size: 50px;
}

.search {
  -webkit-box-sizing: border-box;
  -moz-box-sizing: border-box;
  box-sizing: border-box;
  border-radius: 8px;
  width: 300px;
  height: 30px;
  margin-top: 8px;
  margin-left: 800px;
  background-image: url('http://www.bicycling.com/sites/all/themes/zeus_base/images/svg/search.svg');
  background-position: 3px 5px;
  background-repeat: no-repeat;
  background-size: 20px;
  padding-left: 30px;
}

.form-style-6 {
  -webkit-box-sizing: border-box;
  -moz-box-sizing: border-box;
  box-sizing: border-box;
  font-family: 'Raleway', sans-serif;
  max-width: 400px;
  height: 150px;
  margin-top: 20px;
  margin-left: 100px;
  margin-right: 20px;
  margin-right: 20px;
  padding: 20px;
  background: #F8F8FF;
  box-shadow: 1px 1px 1px 0.5px #DCDCDC;
  display: inline-block;
  width: 350px;
}

.form-style-6 h1 {
  -webkit-box-sizing: border-box;
  -moz-box-sizing: border-box;
  box-sizing: border-box;
  background: #000000;
  padding: 20px 0;
  font-size: 200%;
  font-weight: 300;
  text-align: center;
  color: #fff;
  margin: -16px -10px 0px -10px;
}
.h3 h3{
  font-size: 100%;
  font-weight: 300;
  text-align: center;
  color: #fff;
  margin-top: 20px;
  margin-left: 50px;
}
.canup {
  box-sizing: border-box;
  -webkit-box-sizing: border-box;
  -moz-box-sizing: border-box;
  width: 50%;
  padding: 3%;
  background: #000000;
  margin-bottom: 5px;
  color: #ffffff;
  font-family: 'Raleway', sans-serif;
  display: inline-block;
  font-size: 100%;
}

.canup:hover,
.canup:hover {
  background: #ffffff;
  color: #000000;
}

.bgcolor {
  -webkit-box-sizing: border-box;
  -moz-box-sizing: border-box;
  box-sizing: border-box;
  background-color: #ffffff;
  width: 100%;
  height: 100%;
}

.pre {
  -webkit-box-sizing: border-box;
  -moz-box-sizing: border-box;
  box-sizing: border-box;
  background-color: #000000;
  border: none;
  color: white;
  padding: 3px 10px;
  text-align: center;
  text-decoration: none;
  display: inline-block;
  font-size: 16px;
  cursor: pointer;
  margin-left: 600px;
  margin-top: 0.05px;
}

.pre:hover,
.pre:hover {
  background: #ffffff;
  color: #000000;
}

.next {
  -webkit-box-sizing: border-box;
  -moz-box-sizing: border-box;
  box-sizing: border-box;
  background-color: #000000;
  border: none;
  color: white;
  padding: 3px 10px;
  text-align: center;
  text-decoration: none;
  display: inline-block;
  font-size: 16px;
  cursor: pointer;
}

.next:hover,
.next:hover {
  background: #ffffff;
  color: #000000;
}

.button {
  background-color: #000000;
  border: none;
  border-radius: 8px;
  color: white;
  padding: 16px 16px;
  text-align: center;
  text-decoration: none;
  display: inline-block;
  font-size: 16px;
  margin: 60px 700px;
  -webkit-transition-duration: 0.4s;
  /* Safari */
  transition-duration: 0.4s;
  cursor: pointer;
  width: 80px;
  height: 50px;
}
</style>
