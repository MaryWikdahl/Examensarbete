<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <p>
      We are two students from Ec Utbildning, who studies the last semester of Web development within .Net.<br>
      This semester we've been writing an exam work where we chose to investigate how user-friendly programmers experience the frameworks Vue.js and React.<br>
      The goal of our study is to find out which of these frameworks is best suited when it comes to user-friendleyness, especially by beginners.<br>
      This is the result page where you can take part of the result from our study by clicking on the link "Results"<br>
      
      If you find interest in participating in the study, you can fill out this form. Thanks in advance // Mary and Julia <br>
   
      <a href="https://docs.google.com/forms/d/1CkvuPsYuZvRiYNQB9olRvAqOE6qm6VbFmSPDNuEmJgI/edit" target="_blank" rel="noopener">Link to form</a>.
    </p>
    <h3></h3>
   
    <h3>Read more about Ec Utbildning<br></h3>
    <ul>
      <li><a href="https://ecutbildning.se/" target="_blank" rel="noopener">Here</a></li>
  
    </ul>
    <h3>Read more about the framworks</h3>
    <ul>
      <li><a href="https://vuejs.org/" target="_blank" rel="noopener">Vue.js</a></li>
      <li><a href="https://react.dev/" target="_blank" rel="noopener">React</a></li>
   
    </ul>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  props: {
    msg: String
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
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
</style>
