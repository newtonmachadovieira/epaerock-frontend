<template>
  <div id="app">
    <!-- <img alt="Vue logo" src="./assets/logo.png">
    <HelloWorld msg="Welcome to Your Vue.js App"/> -->
    alo mundo ! 
    <br> okk
    <br> {{alo}}
    <!-- <br> {{localdata[0]}} -->

    <ejs-grid :dataSource="localData2" 
              :allowPaging="true" 
              :pageSettings=pageSettings
              :allowSorting="true"
              :allowFiltering="true"
              :allowGrouping="true"> 
      <e-columns>
        <e-column field="id" headerText="Id Banda" textAlign='Left' ></e-column>
        <e-column field="nome" headerText="Nome Banda" ></e-column>
      </e-columns>
      <!-- <e-columns>
        <e-column field="OrderID" headerText="Order ID" textAlign='Left' ></e-column>
        <e-column field="CustomerID" headerText="Customer ID" ></e-column>
        <e-column field="Price" headerText="Price" format="C2"></e-column>
      </e-columns> -->
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
        {OrderID: 10247, CustomerID: 'VINET', Price: 32.38},
        {OrderID: 10248, CustomerID: 'VINET', Price: 32.38}
      ],
      localData2: null,
      pageSettings: {pageSize: 10 },
      alo: 'eu posso eu consigo eu sou capaz'
    }
  },
  mounted() {
      axios
        .get('http://localhost:3000/api/bandas/led')
        .then(response => (this.localData2 = response))
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
