<template>
  <div class="container-fluid">
      <div class="row justify-content-end">
        <div class="col-3">
            
              <input @keyup.enter="getCards" v-model="inputValue" type="text">
              <button @click="getCards">INVIA</button>
          </div>
      </div>
  </div>
</template>

<script>
import axios from 'axios';


export default {
    name: "Header",
    data() {
        return {
            inputValue: "",
            film: [], 
        }
    },
    methods: {
      getCards: function () {
          axios.get("https://api.themoviedb.org/3/search/movie?api_key=fff1015477ee19b28debc8335af449d5",
            {
                params: {
                    query: this.inputValue
                }
            })
            .then(result => {
              this.film = result.data.results;
              console.log(this.film);
              this.$emit("doSearch", this.film);
              
            })
            .catch(err => {
              console.error(err);               
            })
      }
    },
}
</script>

<style>

</style>