<template>
  <div class="container-100">
      <!-- <div class="container "> -->
        <div class="row">
            <div class="col d-flex align-items-center">
              <img src="../assets/img/logo.png" alt="">
            </div>
            <div class="col d-flex justify-content-end align-items-center">
              <!-- input e bottone che richiamano la funzione ricerca -->
              <input @keyup.enter="getSearch()" v-model="inputValue" type="text">
              <button @click="getSearch()">INVIA</button>
            </div>  
              
            
              
          </div>
      <!-- </div> -->
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

<style lang="scss">
.container-100 {
	width: 100%;
	// margin: auto;
    background-color: black;
    .row{
        width: 100%;
        margin: 0 auto;
    }
  input{
    width: 20%;
    
  }
  button{
      width: 20%;
    }
}

</style>