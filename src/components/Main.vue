<template>
  <div class="container-fluid-main">
      <div class="row ">
        <div class="col ">
          <div class="film"  >
            <div v-if="searchMovie.films.length > 0">
              <Card v-for=" (movie,index) in searchMovie.films" :key="index + movie.id"
              :title="movie.title" 
			        :original="movie.original_title" 
			        :lang="movie.original_language"
			        :vote="movie.vote_average"
			        :image="`https://image.tmdb.org/t/p/w342${movie.poster_path}`"
              :noPhoto="movie.poster_path">
              
              </Card>
             </div >
             <h3 v-else> no film</h3>
                
              <h2>serie tv</h2>
              <div class="film">
                <div v-if="searchMovie.series.length > 0">
                  <Card v-for=" (movie,index) in searchMovie.series" :key="index + movie.id"
                  :title="movie.name" 
			            :original="movie.original_name" 
			            :lang="movie.original_language"
			            :vote="movie.vote_average"
			            :image="`https://image.tmdb.org/t/p/w342${movie.poster_path}`"> 
                </Card>

                </div>
                <h3 v-else> no serie tv</h3>
              
                
              </div>
          </div>
        </div>
      </div>
  </div> 
          <!-- <div class="serie">
                  <ul v-if="searchMovie.series.length > 0">
                    <h2>Serie tv trovate</h2>
                    <li
                    v-for="(serie,index) in searchMovie.series" 
                    :key="index"
                    >
                    
                      <img class="img-fluid "
                    :src="`https://image.tmdb.org/t/p/w342${serie.poster_path}`"
                    :alt="serie.title">

                    <div>{{serie.name}}</div>
                    <div>{{serie.original_name}}</div>
                    <div>{{serie.original_language}}</div>
                    <div>{{serie.release_date}}</div>
                    <div><i :class="'flag flag-' + getFlags(serie.original_language)"></i></div>
                    <div>voto: {{transfNum(serie.vote_average)}}</div>
                    </li>
                  </ul>
                  <h2 v-else>nessuna serie trovato</h2>
          </div> -->
    
</template>

<script>
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
  background-color: black;
  width: 100%;
  .row{
    width: 100%;
    .col{
      display: flex;
      flex-direction: column;
      width: 100%;
  
      .film{
        background-color: brown;
	      display: flex;
		    flex-direction: column;
		    align-items: center;
		    height: 100%;
		    
      }
    }
  }
}

</style>