<template>
  <div id="app">
    <BingoCard />
  </div>
</template>

<script>
import BingoCard from './components/BingoCard.vue';

export default {
  name: 'App',
  components: {
    BingoCard,
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  background-color: #223943;
  height: 100vh;
  padding: 50px;
}

</style>