<template>
  <div class="container">
      <div class="row">
        <div class="col-4">
            <ul>
                  <li
                  v-for="(movie,index) in searchMovie.films" 
                  :key="index"
                  >
                  <!-- <div>{{movie.poster_path}}</div> -->
                  <div>{{movie.title}}</div>
                  <div>{{movie.original_title}}</div>
                  <div>{{movie.original_language}}</div>
                  <div>{{movie.release_date}}</div>
                  <div><i :class="(movie.original_language == 'en') ? 'flag flag-us' : `flag flag-${ movie.original_language }`"></i></div>
                  </li>
              </ul>
          </div>
      </div>
  </div>
</template>

<script>

export default {
    name:"Main",

    props:['searchMovie'],
  
      
  

    data() {
        return {         
        }
    },

}
</script>

<style>

</style>