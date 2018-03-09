<!-- TO DO: Fix code. This is just placeholder code.-->
<template>
  <div>
    <div v-if="errorList.length > 0">
      <h2>There was an error fetching data.</h2>
      <ul class="errors">
        <li v-for="error in errorList">{{ error }}</li>
      </ul>
    </div>
  </div>
</template>
<script>
export default {
  name: 'ErrorList',
  data () {
    return {
    }
  },
  props: {
    errorList: null
  }
}
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
