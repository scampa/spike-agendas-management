<template>
    <div>
      <ul>
        <li>
          <label style="font-weight: bold; margin-left: 20px;">Nombre del grupo:</label>
          <input type="text" id="groupName" name="groupName" v-model="groupName" style="margin: 20px 0 0 20px;">
          <button type="submit" v-on:click.prevent='addGroup(groupName)' style="margin: 20px 20px 20px 20px;">AGREGAR</button>
        </li>
      
        <li>
          <template v-if="!showNewRulePanel">
            <button type="submit" v-on:click.prevent='newGroup()' style="margin: 0px 20px 20px 20px;">+ Nuevo grupo</button>
          </template>
          <template v-if="!showNewRulePanel">
            <button type="submit" v-on:click.prevent='newRule()' style="margin: 0px 0 20px 0;">+ Nueva regla</button>
          </template>
          <template v-if="showNewRulePanel"> 
            <NewRulePanel :list="list"/>
          </template>
        </li>
      </ul>

    </div>
</template>

<script>
import NewRulePanel from './NewRulePanel.vue'

export default {
  name: 'NewGroupPanel',
  props: {
    list: Array
  },
  data () {
    return {
      groupName: null,
      showNewGroupPanel: false,
      showNewRulePanel: false
    }
  },
  components: {
    NewRulePanel
  },
  methods: {
    clear () {
      //this.groupName = null
      this.showNewGroupPanel = false
      this.showNewRulePanel = false
    },
    addGroup(groupName){
        this.list.push(groupName) //Save groupName in list
        console.log(this.list)
        this.clear()
    },
    newGroup () {
        console.log("Estoy en newGroup de NewGroupPanel")
        this.showNewGroupPanel = true
        //this.clear()
    },
    newRule (){
        console.log("Estoy en newRule de NewGroupPanel")
        this.showNewRulePanel = true
    }
  }
}
</script>


