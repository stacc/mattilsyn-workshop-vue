<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <MatTilsyn title="BraMat – Appen du treng når du skal ut å ete"/>
    <listText/>
    <SmileyTabell/>
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
</style>
