<template>
  <div class = "race-information">  
    <ul v-if="results && results.length > 0 " class="results">
      <li v-for="item in results" class="item">
        <p><strong>{{ item.name }}</strong></p>
        <p>{{ item.alignment}}</p>
      </li>
    </ul>
  </div> 
</template>

<script>
</script>

<style>
#app {  
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 40px;
}

body {
  background: #E6E6DB;
}
</style>
