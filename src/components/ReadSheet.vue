<template>
  <div class="bgcolor">
    <ul>
      <li class="active" :style="{'display':invis}">Subject</li>
      <li class="center">
        <div class="" v-for="sheet in sheets" v-if="sheet.subject === selectSubject">
          {{sheet.subject}}
        </div>
      </li>
      <li><a @click="ChangePage(2)" :style="{'display':invis}">Upload</a></li>
    </ul>
    <div class="" v-if="read === 0">
      <div class="form-style-6" v-for="subject in subjects">
        <h1>{{subject.name}}</h1>
        <form>
          <input type="button" value="Read More >" class="canup" @click="selectSubject = subject.name; read = 1; invis = 'none'"/>
        </form>
      </div>
      <!-- <div>
        <br>
        <input type="submit" name="previous" value=" << " class="pre" />&nbsp;&nbsp;&nbsp;<input type="submit" name="next" value=" >> " class="next" />
      </div> -->
    </div>
    <read-more v-if="read === 1" :select-subject="selectSubject" :sheets="sheets"><read-more>
  </div>
</template>

<script>
import ReadMore from './ReadMore'
export default {
  props: ['ChangePage', 'sheets', 'subjects'],
  data () {
    return {
      // subject: ['Subject 1', 'Subject 2', 'Subject 3', 'Subject 4', 'Subject 5', 'Subject 6', 'Subject 7', 'Subject 8', 'Subject 9'],
      selectSubject: '',
      gotoupload: false,
      read: 0,
      invis: ''
    }
  },
  methods: {},
  components: {
    ReadMore
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->

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
  padding: 14px 14px;
  margin-left: 1000px;
  margin-top: 5px;
  text-decoration: none;
}

li a:hover {
  background-color: #F8F8FF;
  color: #000000;
}

.active {
  margin-top: 5px;
  font-size: 32px;
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
  color: #ffffff;
}

.center {
  display: inline-block;
  box-sizing: border-box;
  margin: 0 10px;
  margin-top: 4px;
  font-size: 27px;
  color: #ffffff;
}

a {
  color: #42b983;
}

.search {
  -webkit-box-sizing: border-box;
  -moz-box-sizing: border-box;
  box-sizing: border-box;
  border-radius: 8px;
  width: 300px;
  height: 30px;
  margin-top: 8px;
  margin-left: 500px;
  background-image: url('http://www.bicycling.com/sites/all/themes/zeus_base/images/svg/search.svg');
  background-position: 3px 5px;
  background-repeat: no-repeat;
  background-size: 20px;
  padding-left: 30px;
  padding-right: 50px;
}

.form-style-6 {
  -webkit-box-sizing: border-box;
  -moz-box-sizing: border-box;
  box-sizing: border-box;
  font-family: 'Raleway', sans-serif;
  max-width: 400px;
  height: 150px;
  margin-top: 20px;
  margin-left: 60px;
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
  margin: -16px -16px 16px -16px;
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
</style>
