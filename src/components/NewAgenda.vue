<template>
    <div>
      <template v-if="!showAgendaName">
        <ul>
          <li>
            <label style="font-weight: bold; margin-left: 20px;">Nombre de la agenda:</label>
            <input type="text" id="agendaName" name="agendaName" v-model="agendaName" style="margin: 0 0 0 20px;">
            <button type="submit" v-on:click.prevent='createAgenda(agendaName)' style="margin: 20px 20px 20px 20px;">Crear agenda</button>
          </li>
        </ul>
      </template>

      <template v-else>
        <label style="font-weight: bold; font-size: 22pt; margin: 20px 20px 20px 20px;">{{ agendaName }}</label>

      <!--  <button type="submit" v-on:click.prevent='newGroup()' style="margin: 0px 20px 20px 20px;">+ Nuevo grupo</button>
        <button type="submit" v-on:click.prevent='newRule()' style="margin: 0px 0 20px 0;">+ Nueva regla</button> -->
      </template>

      <template v-if="showGroupPanel">
        <NewGroupPanel :list="list" />
      </template>
      <!-- <template v-if="showRulePanel">
        <NewRulePanel :list="list" />
      </template>-->

    </div>
</template>

<script>
import NewGroupPanel from './NewGroupPanel.vue'
//import NewRulePanel from './NewRulePanel.vue'

export default {
  name: 'NewAgenda',
  props: {
    list: Array
  },
  data () {
    return {
      agendaName: null,
      showAgendaName: false,
      showGroupPanel: false,
      //showRulePanel: false
    }
  },
  components: {
    NewGroupPanel,
    //NewRulePanel
  },
  methods: {
    clear () {
      this.showGroupPanel = false
      //this.showRulePanel = false
    },
    createAgenda (agendaName) {
        console.log("Estoy en createAgenda de NewAgenda")
        this.agendaName = agendaName
        this.showAgendaName = true
        this.showGroupPanel = true
        console.log(this.agendaName)
        //this.clear()
    },
    /*newGroup(){
        console.log("Estoy en newGroup de NewAgenda")
        this.showGroupPanel = true
    },*/
    /*newRule() {
        console.log("Estoy en newRule de NewAgenda")
        this.showRulePanel = true
    } */
  } 
}
</script>


