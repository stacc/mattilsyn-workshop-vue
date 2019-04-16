<template>
  <section class="table">
    <button v-on:click="getPlaceByPostalCode('Bergen')">Bergen</button>
    <button v-on:click="getPlaceByPostalCode('Oslo')">Oslo</button>
    <button v-on:click="emptyList()">Tøm liste</button>
    <section v-if="hasData">
        <input type="text" id="myInput" onkeyup="filterTable()" placeholder="Søk etter restaurant..">
        <table id="myTable">
        <tr class="header">
            <th style="width:40%;">Matplass</th>
            <th style="width:20%;">Dato</th>
            <th style="width:10%;">Heilhetskarakter</th>
            <th style="width:10%;">Karakter 1</th>
            <th style="width:10%;">Karakter 2</th>
            <th style="width:10%;">Karakter 3</th>
        </tr>
        <tr v-for="place in places">
            <td>{{ place.navn }}</td>
            <td>{{ place.dato }}</td>
            
            <td>{{ place.total_karakter }}</td>
            <td>{{ place.karakter1 }}</td>
            <td>{{ place.karakter2 }}</td>
            <td>{{ place.karakter3 }}</td>
        </tr>
        </table>
    </section>  
    </section>      
</template>
    


<script>
import axios from 'axios'

export default {
  name: 'SmileyTabell',
  props: {
    
  },
  data () {
      return {
          places: [],
          hasData: false
      }
  },
  computed: {

  }, 
  methods: {
      getPlaceByPostalCode(postalCode) {
          axios ({ method: 'GET', url: 'https://hotell.difi.no/api/json/mattilsynet/smilefjes/tilsyn?poststed=' + postalCode }).then(resturant => {
                this.hasData = true;
               this.places = '';
               this.places = resturant.data.entries;
          }, error => {
              console.log(error);
          })
      },
      emptyList(){
          this.places = '';
          this.hasData = false;
      },
      filterTable(){
        var input, filter, table, tr, td, i, txtValue;
        input = document.getElementById("myInput");
        filter = input.value.toUpperCase();
        table = document.getElementById("myTable");
        tr = table.getElementsByTagName("tr");

        for (i = 0; i < tr.length; i++) {
            td = tr[i].getElementsByTagName("td")[0];
            if (td) {
            txtValue = td.textContent || td.innerText;
            if (txtValue.toUpperCase().indexOf(filter) > -1) {
                tr[i].style.display = "";
            } else {
                tr[i].style.display = "none";
            }
            } 
        }
      }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.table {
    padding: 20px;
    width: 70%;
    height: auto;
    margin: auto;
}
a {
  color: #42b983;
}

#myTable {
  border-collapse: collapse;
  width: 100%;
  border: 1px solid #ddd;
  font-size: 18px;
}

#myTable th, #myTable td {
  text-align: left;
  padding: 12px;
}

#myTable tr {
  border-bottom: 1px solid #ddd;
}

#myTable tr.header, #myTable tr:hover {
  background-color: #f1f1f1;

}

</style>
