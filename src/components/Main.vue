<template>
  <div class="container-fluid-main ">
    <div class="row row-cols-5">
      <!-- Card-film -->
      <div class="film-serie" v-if="searchMovie.films.length > 0">
        <div class="text"><h2>Film</h2></div>
        <Card v-for=" (movie,index) in searchMovie.films" :key="index +   movie.id"
          :title="movie.title" 
			    :original="movie.original_title" 
			    :lang="movie.original_language"
			    :vote="movie.vote_average"
          :overview="movie.overview"
			    :image="`https://image.tmdb.org/t/p/w342${movie.poster_path}`"
          :noPhoto="movie.poster_path">     
        </Card>
      </div >
      <h3 v-else> No film</h3>
                
      
      <!-- Card-serie-tv        -->
      <div class="film-serie" v-if="searchMovie.series.length > 0">
        <div class="text"><h2>Serie tv</h2></div>
        
        <Card v-for=" (movie,index) in searchMovie.series" :key="index + movie.id"
          :title="movie.name" 
			    :original="movie.original_name" 
			    :lang="movie.original_language"
			    :vote="movie.vote_average"
          :overview="movie.overview"
			    :image="`https://image.tmdb.org/t/p/w342${movie.poster_path}`"> 
        </Card>

      </div>
      <h3 v-else> No serie tv</h3>  
    </div>
  </div>      
</template>

<script>
// import figlio Card
import Card from './Card.vue'
export default {
    name:"Main",
    components:{
      Card,
    },

    props:['searchMovie'],
    data() {
        return {         
        }
    },
    methods: {
      //   getFlags(value){
      //       switch (value){
      //           case 'en':
      //               return 'uk';
      //           case 'ko':
      //               return 'kr';
      //           case 'ja':
      //               return 'jp';
      //           case 'ur':
      //               return 'pk';
      //           case 'zh':
      //               return 'cn';
      //           default:
      //               return value;
      //       }
      //   },
      // transfNum(num){
      //   const numberStar = num / 2;
      //   return numberStar.toFixed(0)
      // }
    }
    

}
</script>

<style lang="scss" >
.container-fluid-main{
  background-color: rgb(70, 68, 68);
  width: 100%;
  .row{
    // width: 100%;
    width: 70%;
    margin: 0 auto;
    .film-serie{
      display: flex;
      flex-wrap: wrap;
      width: 100%;
      .text{
        width: 100%;
        h2{
        text-align: center;
      }
      }
      
    }
  }
  h3,h2{
    color: white;
  }
}

</style>