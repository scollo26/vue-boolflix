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
      arrayMovie: ""
    }
  },
  components: {
    Header,
    Main,
  },
  methods: {
    Select(value) {
      this.arrayMovie = value
      console.log(this.arrayMovie)
    }
  },
};
</script>

<style lang="scss">
  @import "~bootstrap/scss/bootstrap";
  @import '~mdb-ui-kit/css/mdb.min.css';
</style>