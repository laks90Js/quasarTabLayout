<template>
  <q-page padding class="outer-tab-pane row justify-center">
    <div style="width: 1200px; max-width: 90vw;">
      <q-tabs animated swipeable inverted color="secondary" align="justify" two-lines  v-model="selectedTab">
        <q-tab @click="tabClick('React')" default name="React" slot="title" label="React" />
        <q-tab @click="tabClick('Angular')" name="Angular" slot="title"  label="Angular" />
        <q-tab @click="tabClick('Vue')" name="Vue" slot="title" label="Vue" />

        <q-tab-pane name="React">
          {{currentTabData.title}}
          {{currentTabData.content}}
        </q-tab-pane>
        <q-tab-pane name="Angular">Angualr tab</q-tab-pane>
           {{currentTabData.title}}
           {{currentTabData.content}}
        <q-tab-pane name="Vue">Vue tab</q-tab-pane>
           {{currentTabData.title}}
           {{currentTabData.content}}
      </q-tabs>
    </div>
  </q-page>
</template>

<script>
import axios from 'axios'

export default {
  data () {
    return {
      aLangTypes: [
        'Angular',
        'React',
        'Vue'
      ],
      currentTabData: {},
      selectedTab: true
    }
  },
  methods: {
    tabClick (langType) {
      axios.get('../assets/stubs/tabs.json').then(response => {
        this.currentTabData = response[langType]
      }).catch(function () {
        console.log('error')
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
