<template>
  <div class="hello">
    <h2>Karakterskala</h2>
    <section class="list">
      <ul>
        <li>0 = Ingen brudd på regelverket funnet. Stort smil.</li>
        <li>1 = Mindre brudd på regelverket som ikke krever oppfølging. Stort smil.</li>
        <li>2 = Brudd på regelverket som krever oppfølging. Strekmunn.</li>
        <li>3 = Alvorlig brudd på regelverket. Sur munn.</li>
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
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
