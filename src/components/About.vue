<template>
  <div class="hello">
    <div id="app">
    <div>
    <ul>
      <li><a class="active" @click="ChangePage(1)">Home</a></li>
      <li><input type="search" class="search"></li>
      <li><a @click="ChangePage(2)">Upload</a></li>
      <li><a @click="ChangePage(3)">About</a></li>
    </ul>
  </div>
  <div>
      <h1>{{msg}}</h1>
      <h2>{{msg2}}</h>
    </div>
  </div>
</template>

<script>
export default {
  props: ['ChangePage'],
  name: 'hello',
  data () {
    return {
      msg: 'Sheetato',
      msg2: 'Sheetato is web upload and read file for free'
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1, h2 {
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
@import url('https://fonts.googleapis.com/css?family=Raleway');

ul {
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
  width: 230px;
  height: 30px;
  margin-top: 8px;
  margin-left: 790px;
}

#app {
  font-family: 'Raleway',Helvetica, Arial, sans-serif;
  font-size: 40px;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin: auto;
}
</style>
