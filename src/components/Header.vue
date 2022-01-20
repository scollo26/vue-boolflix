<template>
  <div class="container-fluid">
      <div class="row justify-content-end">
        <div class="col-3">
            
              <input @keyup.enter="getSearch" v-model="inputValue" type="text">
              <button @click="getSearch">INVIA</button>
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
            inputValue: null,
            query:'https://api.themoviedb.org/3/search/',
            api_key:'fff1015477ee19b28debc8335af449d5' ,
            arrayFull: {
                Movies: [],
                Tv: [],
            },
        }
    },
    methods: {
      getFilms: function () {
        const endpoint= 'movie';
        const parameters = {
          api_key: this.api_key,
          query: this.inputValue,
        }
          axios.get(`${this.query}${endpoint}`, {params: parameters})
            .then(result => {
              // this.arrayFull = result.data.results;
              this.arrayFull.Movies = result.data.results;
              // console.log(this.arrayFull);
              // this.$emit("doSearch", this.arrayFull);
              
            })
            .catch(err => {
              console.error(err);               
            })
      },
      getSerieTv: function () {
        const endpoint= 'tv';
        const parameters = {
          api_key: this.api_key,
          query: this.inputValue,
        }
          axios.get(`${this.query}${endpoint}`, {params: parameters})
            .then(result => {
              this.arrayFull.Tv = result.data.results;
              // setTimeout(() => {
              //   this.$emit("doSearch", this.arrayFull);
              // }, 800);
              
              
            })
            .catch(err => {
              console.error(err);               
            })
      },
      getSearch: function(){
        this.getFilms();
        this.getSerieTv();
        setTimeout(() => {
              this.$emit('doSearch', this.arrayFull);
              console.log(this.arrayFull);
                
            }, 800);
        
      }
    },
   
}
</script>

<style>

</style>