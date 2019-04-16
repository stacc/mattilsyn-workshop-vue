<template>
  <div id="app">
    <MatTilsyn title="BraMat – Appen du treng når du skal ut å ete"/>
    <listText/>
    <SmileyTabell/>
    <img class="logoStacc" src="./assets/stacc_logo_bright-bg.png" alt="Stacc">
  </div>
</template>

<script>
import MatTilsyn from './components/MatTilsyn.vue'
import SmileyTabell from './components/SmileyTabell.vue'
import ListText from './components/ListText.vue'

export default {
  name: 'app',
  components: {
    MatTilsyn,
    SmileyTabell,
    ListText
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
.logoStacc {
  margin: 50px;
}
</style>
