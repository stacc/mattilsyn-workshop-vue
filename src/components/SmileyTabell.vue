<template>
  <section class="table">
    <button :class="{ active: isActive('Bergen') }" v-on:click="getPlaceByPostalCode('Bergen')">Bergen</button>
    <button :class="{ active: isActive('Oslo') }" v-on:click="getPlaceByPostalCode('Oslo')">Oslo</button>
   
    <section v-if="hasData">
        <input type="text" id="myInput" v-on:keyup="filterTable()" placeholder="Søk etter restaurant..">
         <button v-on:click="emptyList()">Tøm liste</button>
        <table id="myTable">
        <tr class="header">
            <th style="width:40%;">Matplass</th>
            <th style="width:20%;">Dato</th>
            <th style="width:10%;">Heilhetskarakter</th>
            <th style="width:10%;">Karakter 1</th>
            <th style="width:10%;">Karakter 2</th>
            <th style="width:10%;">Karakter 3</th>
        </tr>
        <tr v-for="place in places" v-bind:key="place.index" >
            <td>{{ place.navn }}</td>
            <td>{{ place.dato }}</td>
            
            <td>
                <div v-if="place.total_karakter == 0"><img class="gradeFace" src="../assets/stort_smil.png" alt="stort smil" width="30"/></div>
                <div v-if="place.total_karakter == 1"><img class="gradeFace" src="../assets/stort_smil.png" alt="stort smil" width="30"/></div>
                <div v-if="place.total_karakter == 2"><img class="gradeFace" src="../assets/strek_fjes.png" alt="stort smil" width="30"/></div>
                <div v-if="place.total_karakter == 3"><img class="gradeFace" src="../assets/surt_fjes.png" alt="stort smil" width="30"/></div>

            </td>
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
          hasData: false,
          activeItem: ''
      }
  },
  methods: {
      getPlaceByPostalCode(postalCode) {
          axios ({ method: 'GET', url: 'https://hotell.difi.no/api/json/mattilsynet/smilefjes/tilsyn?poststed=' + postalCode }).then(resturant => {
               this.activeItem = postalCode;
               this.hasData = true;
               this.places = '';
               this.places = resturant.data.entries;
          }, error => {
              console.log("Noko gjekk gale", error);
          })
      },
      emptyList(){
          this.places = '';
          this.activeItem = '';
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
       },
        isActive (menuItem) {
            return this.activeItem === menuItem;
       }
    }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
a {
  color: #42b983;
}

button {
    width: 140px;
    height: 45px;
    margin: 10px;
    background-color: white;

    color: #467EFF;
    font-family: Arial, Helvetica, sans-serif;
    font-size: 14pt;
    font-weight: bold;

    border: 3px solid #C7D8FF; 
    border-radius: 6px;

    -webkit-transition-duration: 0.2s;
    transition-duration: 0.2s;
}

button:hover, .active{
    background-color: #467EFF;
    border: 3px solid #467EFF; 
    border-radius: 6px;
    color: white;
}

button:active, button:visited, {
    outline: none;
    border: none;
}

.gradeFace {
    vertical-align: middle;
}

.table {
    padding: 20px;
    width: 70%;
    height: auto;
    margin: auto;
}

#myInput {
  width: 40%; 
  font-size: 16px; 
  padding: 12px 20px 12px 40px;
  border: 1px solid #ddd;
  margin-bottom: 12px;
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
