<template>
  <div id="app">
   <Header 
   @sendSelect="Select($event)"
   />
   <Main 
   
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