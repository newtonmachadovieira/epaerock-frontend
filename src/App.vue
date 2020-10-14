<template>
  <div id="app">
    <!-- <img alt="Vue logo" src="./assets/logo.png">
    <HelloWorld msg="Welcome to Your Vue.js App"/> -->
    alo mundo ! 
    <br> {{alo}}

    <ejs-grid :dataSource='localData2'
              :allowPaging="true" 
              :pageSettings=pageSettings
              :allowSorting="true"
              :allowFiltering="true"
              :allowGrouping="true"> 
      <e-columns>
        <e-column field="letra" headerText="Letra" textAlign='Center'></e-column>
        <e-column field="nome" headerText="Banda/Grupo" ></e-column>
        <e-column field="obs" headerText="Obs Albuns" textAlign='Center' ></e-column>
        <e-column field="dt_primeiro_album" headerText="Data 1o Album" textAlign='Left' ></e-column>
        <e-column field="dt_ultimo_album" headerText="Data Ultimo Album" textAlign='Left' ></e-column>
      </e-columns>
    </ejs-grid>
 

  </div>
</template>

<script>

import Vue from 'vue';
import { GridPlugin, Page, Sort, Filter, Group} from '@syncfusion/ej2-vue-grids';
Vue.use(GridPlugin);
var axios = require("axios");


export default {
  name: 'App',
  data () {
    return {
      localData: [
        {"OrderID":10245,"CustomerID":'VINET',"Price":32.38},
        {"OrderID":10248,"CustomerID":'VINET',"Price":32.38}
      ],
      localData2: null,
      pageSettings: {pageSize: 3000 },
      alo: 'eu posso eu consigo eu sou capaz'
    }
  },
  mounted() {
      axios
        .get('http://localhost:3000/api/bandas/')
        .then(response => (this.localData2 = response.data))

  },
  components: {
    //HelloWorld
  },
  provide: {
    grid: [Page, Sort, Filter, Group]
  }

}
</script>

<style>
  @import url(https://cdn.syncfusion.com/ej2/material.css);
/* #app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
} */
</style>
