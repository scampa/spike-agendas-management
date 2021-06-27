<template>
  <div id="app">
    <NewAgenda :list="list" />
    <!-- <NewGroupPanel :list="list" /> -->
    <!-- <NewRulePanel :list="list" /> -->
    <TreeView :list="list" />
  </div>
</template>



<script>
//import NewGroupPanel from './components/NewGroupPanel.vue'
//import NewRulePanel from './components/NewRulePanel.vue'
import NewAgenda from './components/NewAgenda.vue'
import TreeView from './components/TreeView.vue'

export default {
  name: 'App',
  components: {
    //NewGroupPanel,
    //NewRulePanel,
    NewAgenda,
    TreeView
  },
  data() {
    return {
      param: "PARAMETRO DE APP",
      list: []
    }
  }
}
</script>
