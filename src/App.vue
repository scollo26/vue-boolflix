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
  methods: {
    Select(value) {
      this.arrayMovie = value
      console.log(this.arrayMovie)
    }
  },
  components: {
    Header,
    Main,
  },
};
</script>

<style lang="scss">
  @import "~bootstrap/scss/bootstrap";
</style>