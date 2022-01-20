<template>
  <div id="app">
    <Header 
      @doSearch="Select($event)"
    />
    <Main 
      :searchMovie="arrayMovie"
    />
  </div>
</template>

<script>
import Header from './components/Header.vue'
import Main from './components/Main.vue'
export default {
  name: "App",
  data() {
    return {
      arrayMovie: {
        films:[],
        series:[],
      },
    }
  },
  components: {
    Header,
    Main,
  },
  methods: {
    Select(value) {
      this.arrayMovie.films = value.Movies;
      this.arrayMovie.series = value.Tv;
      console.log(this.arrayMovie.films);
      // console.log(this.arrayMovie.series)
    }
  },
};
</script>

<style lang="scss">
  @import "~bootstrap/scss/bootstrap";
  @import '~mdb-ui-kit/css/mdb.min.css';
</style>