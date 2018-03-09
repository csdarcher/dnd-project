<template>
  <div class = "race-selector">  
    <div class="Title">
        <h1>Dungeons and Dragons 5th Edition Race Informer</h1>
    </div>
      <div class="form-container"> 
        <h2> Select 2 races below to compare.</h2>
              <form v-on:submit.prevent="compareRaces">
                  <!-- <div id='checkboxes'> -->
                      <div v-for="(result,index) in results" :key="index">
                        <input type="checkbox" :id="result.name" :value="result.index" v-model="checkedRaces">
                        <label :for="result.name">{{result.name}}</label>
                      </div>
                      <!-- <input type="checkbox" id="dwarf" value="dwarf" v-model="checkedRaces">
                      <label for="dwarf">Dwarf</label>
                      <input type="checkbox" id="elf" value="elf" v-model="checkedRaces">
                      <label for="elf">Elf</label>
                      <input type="checkbox" id="halfling" value="halfling" v-model="checkedRaces">
                      <label for="halfling">Halfing</label>
                      <input type="checkbox" id="human" value="human" v-model="checkedRaces">
                      <label for="human">Human</label>
                      <input type="checkbox" id="dragon-born" value="dragon-born" v-model="checkedRaces">
                      <label for="dragon-born">Dragon-Born</label>
                      <input type="checkbox" id="gnome" value="races" v-model="checkedRaces">
                      <label for="gnome">Gnome</label>
                      <input type="checkbox" id="half-elf" value="gnome" v-model="checkedRaces">
                      <label for="half-elf">Half-Elf</label>
                      <input type="checkbox" id="half-orc" value="half-orc" v-model="checkedRaces">
                      <label for="half-orc">Half-Orc</label>
                      <input type="checkbox" id="tiefling" value="tiefling" v-model="checkedRaces">
                      <label for="tiefling">Tiefling</label> 
                      <br> -->
                  <!-- </div>  -->
                <!-- <div class="grid-container"> 
                  <div class="grid-item" :key="index" v-for="(item,index) in races">
                    {{ item.name }} --> 
              <button type="submit">Compare</button> 
          <!-- </div>   -->
            <load-spinner v-if="showLoading"></load-spinner>
        </form>  
        <ul class="races" v-if="results && results.length > 0 ">
            <li v-for="(item,index) in results" :key="index" class="item">
              <p><strong>{{ races.name }}</strong></p>
              <p>{{ races.alignment }}</p>
            </li>
       </ul>
     </div>
  </div>      
</template>

<script>
import axios from 'axios';
// import { API } from "@/components/api"
// import axios from 'axios'
// import DoubleBounce from "@/components/DoubleBounce"

export default {
  name: "RaceSelector",
  // components: {
  //   'load-spinner': DoubleBounce
  // },

  data() {
    return {
      results: null,
      showLoading: false,
      checkedRaces: [],
      races: [],
      errors: []
    };
  },
  created(){
     axios.get('http://dnd5eapi.co/api/races')
        .then(response => {
          // this.showSpinner = false;
          this.results = response.data.data
        })
        .catch(e => {
          // console.log("error");
          // this.showSpinner = false;
          this.errors.push(e)
        })
  },

  methods: {
    compareRaces: function() {
      //  API.get('find', {
      // axios
      //   .get("http://dnd5eapi.co/api/races", {
      //     params: {
      //       races: this.name,
      //       alignment: this.alignment
      //     }
      //   })
      //   .then(function(response) {
      //     console.log(response);
      //   })
      //   .catch(function(error) {
      //     console.log(error);
      //   });

      //   params: {
      //       races: this.name,
      //       alignment: this.alignment,

      //   }
      // })

      // .then(response => {
      //   this.results = response.data;
      // })
      // .catch(error => {
      //   this.errors.push(error.message);
      // });
    }
  }
};
// TO DO: Add error message for when user fails to choose a race or chooses more than 2 races.
</script>

<!-- Added "scoped" attribute to limit CSS to this component only -->
<style scoped>
body {
  background: #e6e6db;
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

.form-container {
  border: 2px;
  border-color: #7a7362;
}

button {
  background: #df0404;
  margin: 10px;
  padding: 0.5rem;
  color: #fff;
  border: none;
  font-size: 15px;
}
</style>
