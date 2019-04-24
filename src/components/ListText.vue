<template>
  <div class="hello">
    <h2>Karakterskala</h2>
    <section class="list">
      <ul>
        <li><img class="gradeFace" src="../assets/stort_smil.svg" alt="stort smil" width="30"/> 0 = Ingen brudd på regelverket funnet.</li>
        <li><img class="gradeFace" src="../assets/stort_smil.svg" alt="stort smil" width="30"/> 1 = Mindre brudd på regelverket som ikke krever oppfølging.</li>
        <li><img class="gradeFace" src="../assets/strek_fjes.svg" alt="strekfjes" width="30"/> 2 = Brudd på regelverket som krever oppfølging.</li>
        <li><img class="gradeFace" src="../assets/surt_fjes.svg" alt="surt fjes" width="30"/> 3 = Alvorlig brudd på regelverket.</li>
      </ul>
      </section>
  </div>
</template>



<script>
export default {
  name: 'ListText',
  props: {
    title: String
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.list {
    width: 600px;
    text-align: left;
    margin: auto;
}
.gradeFace {
    vertical-align: middle;
    padding: 5px;
}
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin-top: 20px;
  margin-left: 60px;
}
a {
  color: #42b983;
}
</style>
