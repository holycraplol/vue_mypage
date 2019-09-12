<template>
  <div id="app">
      <img alt="Vue logo" src="./assets/logo.png">
      <Header/>
  

     
  
<b-table-simple responsive>
    <b-thead>
    <b-tr>
      <b-th>Username</b-th>
      <b-th>Title</b-th>
      <b-th>Summary</b-th>
    </b-tr>
    </b-thead>
    <b-tbody>
    <b-tr v-for='item in items' v-bind:key="item"> 
      <b-td>{{ item.t_USERNAME }}</b-td>
      <b-td>{{ item.t_TITLE }}</b-td>
      <b-td>{{ item.t_SUMMARY }}</b-td>
    </b-tr>
    </b-tbody>
  </b-table-simple>
  </div>


  
</template>

<script>
    import Vue from 'vue'
    import Header from './components/Header';
    import axios from 'axios';
    import BootstrapVue from 'bootstrap-vue';
    import PortalVue from 'portal-vue';
    Vue.use(BootstrapVue)
     Vue.use(PortalVue)

export default {
  name: 'app',
  components: { 
      
      Header,
      
      
  },
  data() {
      return {
          items: [
       // { Title: items.t_TITLE, Summary: items.t_SUMMARY, User: items.t_USER },
          { age: 21, first_name: 'Larsen', last_name: 'Shaw' },
          { age: 89, first_name: 'Geneva', last_name: 'Wilson' },
          { age: 38, first_name: 'Jami', last_name: 'Carney' }
          ]
      }
      methods: {
     
      }
      
        },
        created: function()
      {
        axios.get('http://student40072.bucomputing.uk/tableQuery.php?tableQuery=all')
        .then(function (response)
        {
        console.log(JSON.stringify(response.data))
        self.items = response.data
        })
        .catch(function (error)
        {
          console.log(error)

        });
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
