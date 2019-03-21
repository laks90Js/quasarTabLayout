<template>
  <q-page class="flex">
    <q-tabs>
  <!-- Tabs - notice slot="title" -->
  <q-tab default slot="title" name="tab-1" icon="message" />
  <q-tab slot="title" name="tab-2" icon="fingerprint" />
  <q-tab slot="title" name="tab-3" icon="account_box" />
  <!-- Targets -->
  <q-tab-pane name="tab-1">Tab One</q-tab-pane>
  <q-tab-pane name="tab-2">Tab Two</q-tab-pane>
  <q-tab-pane name="tab-3">Tab Three</q-tab-pane>
</q-tabs>
  </q-page>
</template>

<style>
</style>

<script>
import axios from 'axios';

export default {
  name: 'PageIndex',
  methods : {
    loadData()  {
      axios.get("../assets/tabs.json")
      .then(reponse => {
        console.log(response);
      }).catch(error=>{
        console.log(error)
      })
    },
    mounted () {
      this.loadData()
    }
  }
}
</script>




export default ({app, router, Vue}) => {
  Vue.prototype.$axios = axios
  // ^ ^ ^ this will allow you to use this.$axios
  //       so you won't necessarily have to import axios in each vue file
}