<template>
      <select name="groupToRule" @change="selectRule(selectedRuleName)" v-model="selectedRuleName">
        <option disabled value="">Seleccione una opción</option>
        <option v-for="rule in rulesDropDown" :value="rule.name" :key="rule.name">{{ rule.name }}</option>
    </select>
</template>

<script>
export default {
  name: 'RulesDropDown',
  props: {
    rulesDropDown: Array,
    form: Object
  },
  data() {
    return {
      selectedRuleName: null
    }
  },
  watch: {
    rulesDropDown: {
        handler() {
          console.log("I'm inside the handler!!")
          this.selectedRuleName = null
      }
    }
  },
  methods: {
    selectRule(selectedRuleName){ //Parameter has the same name as the data() variable
      console.log(selectedRuleName)
      this.form.groupByRule = selectedRuleName //Set the selected rule in the "rule form" received
    }
  }
}
</script>
