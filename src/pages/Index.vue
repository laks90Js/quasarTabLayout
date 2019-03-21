<template>
  <q-page padding class="outer-tab-pane row justify-center">
    <div style="width: 1200px; max-width: 90vw;">
      <q-tabs animated swipeable inverted color="secondary" align="justify" two-lines="true" panes-container-class="" v-model="selectedTab">
        <q-tab @click="tabClick('React')" default name="React" slot="title" label="React" />
        <q-tab @click="tabClick('Angular')" name="Angular" slot="title"  label="Angular" />
        <q-tab @click="tabClick('Vue')" name="Vue" slot="title" label="Vue" />

        <q-tab-pane name="React">
          {{currentTabData.title}}
        </q-tab-pane>
        <q-tab-pane name="Angular">Angualr tab</q-tab-pane>
        <q-tab-pane name="Vue">Vue tab</q-tab-pane>
      </q-tabs>
    </div>
  </q-page>
</template>

<script>
import axios from 'axios'
let currentTabData = {};

export default {
  data () {
    return {
      aLangTypes: [
        'Angular',
        'React',
        'Vue'
      ]
    }
  },
  methods: {
    tabClick (langType) {
      axios.get('../assets/stubs/tabs.json').then(response =>{
        this.currentTabData = response[langType];
      }).catch(function () {
        console.log("error");
      })
    }
  }
}
</script>

<style lang="stylus">
.outer-tab-pane
  .q-tab-pane
    display flex
    align-items center
    justify-content center
    height 65px
</style>
