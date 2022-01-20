<template>
  <div class="container">
      <div class="row">
        <div class="col-4">
            <ul>
                  <li
                  v-for="(movie,index) in searchMovie" 
                  :key="index"
                  >
                  <!-- <div>{{movie.poster_path}}</div> -->
                  <div>{{movie.title}}</div>
                  <div>{{movie.original_title}}</div>
                  <div>{{movie.original_language}}</div>
                  <div>{{movie.release_date}}</div>
                  
                  </li>
              </ul>
          </div>
      </div>
  </div>
</template>

<script>

export default {
    name:"Main",

    props: {
      searchMovie: {
        // searchMovie: String,
        type: Array,
        default() {
          return [];
        },

      },
      
    },

    data() {
        return {         
        }
    },

}
</script>

<style>

</style>