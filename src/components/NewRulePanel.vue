<template>
    <div>
      <form>
        <ul>
          <li>
            <label for="ruleName">Nombre:</label>
            <input type="text" id="ruleName" name="ruleName" v-model="form.ruleName">
          </li>
          <li>
            <label>Tipo:</label>
            <div class="radio-button-group">
              <input type="radio" id="a" value="a" v-model="form.type"> <label for="a">Aditiva</label>
              <input type="radio" id="s" value="s" v-model="form.type"> <label for="s">Sustractiva</label>
            </div>
          </li>
          <li>
          <label>Días:</label>
          <div class="checkbox-group checkbox-week-days">
              <div><label for="sun">D</label> <input type="checkbox" id="sun" value="sun" v-model="form.weekDays"></div>
              <div><label for="mon">L</label> <input type="checkbox" id="mon" value="mon" v-model="form.weekDays"></div>
              <div><label for="tue">M</label> <input type="checkbox" id="tue" value="tue" v-model="form.weekDays"></div>
              <div><label for="wed">M</label> <input type="checkbox" id="wed" value="wed" v-model="form.weekDays"></div>
              <div><label for="thu">J</label> <input type="checkbox" id="thu" value="thu" v-model="form.weekDays"></div>
              <div><label for="fri">V</label> <input type="checkbox" id="fri" value="fri" v-model="form.weekDays"></div>
              <div><label for="sat">S</label> <input type="checkbox" id="sat" value="sat" v-model="form.weekDays"></div>
            </div>
          </li>
          <li>
            <label for="dateFrom">Desde:</label> <input type="date" id="dateFrom" name="dateFrom" v-model="form.dateFrom">
            <label for="dateTo">Hasta:</label> <input type="date" id="dateTo" name="dateTo" v-model="form.dateTo">
          </li>
          <li>
            <label for="timeFrom">Desde:</label> <input type="time" id="timeFrom" name="timeFrom" v-model="form.timeFrom">
            <label for="timeTo">Hasta:</label> <input type="time" id="timeTo" name="timeTo" v-model="form.timeTo">
          </li>
        </ul>
        <button type="submit" v-on:click.prevent='addRule(form)' style="margin: 20px 0 0 0;">Agregar regla</button>
      </form>
    </div>
</template>

<script>
export default {
  name: 'NewRulePanel',
  props: {
    list: Array
  },
  data () {
    return {
      form: {
        ruleName: null,
        type: 'a',
        weekDays: [],
        dateFrom: null,
        dateTo: null,
        timeFrom: null,
        timeTo: null,
        groupByRule: null
      }
    }
  },
  methods: {
    clear () {
      this.form = {
        ruleName: null,
        type: 'a',
        weekDays: [],
        dateFrom: null,
        dateTo: null,
        timeFrom: null,
        timeTo: null,
        groupByRule: null
      }
    },
    addRule (item) {
        console.log("addRule method inside NewRulePanel.vue")
        //this.$emit('new', JSON.parse(JSON.stringify(this.form)))
        this.list.push(item) 
        this.clear()
        //console.log(this.list[0].ruleName)
    }
  }
}
</script>


<style>
html, body {
  box-sizing: border-box;
  font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 'Open Sans', 'Helvetica Neue', sans-serif;
  padding: 0;
  margin: 0;
  height: 100%;
}

form {
  margin: 0 auto;
  padding: 1em;
  border-radius: 1em;
}

ul {
  list-style: none;
  padding: 0;
  margin: 0;
}

form li + li {
  margin-top: 1em;
}

label {
  display: block;
}

input,
textarea {
  /* To make sure that all text fields have the same font settings
     By default, textareas have a monospace font */
  font: 1em sans-serif;

  /* Uniform text field size */
  /* width: 300px; */
  box-sizing: border-box;

  /* Match form field borders */
  border: 1px solid #999;
}

input:focus,
textarea:focus {
  /* Additional highlight for focused elements */
  border-color: #000;
}

textarea {
  /* Align multiline text fields with their labels */
  vertical-align: top;

  /* Provide space to type some text */
  height: 5em;
}

.button {
  /* Align buttons with the text fields */
  padding-left: 90px; /* same size as the label elements */
}

button {
  /* This extra margin represent roughly the same space as the space
     between the labels and their text fields */
  margin-left: .5em;
}

.radio-button-group label,
.radio-button-group input {
  display: inline-block;
}

.checkbox-group.checkbox-week-days {
  display: inline-flex;
  flex-direction: row;
}

.checkbox-group.checkbox-week-days > div {
  display: inline-block;
  flex: 1;
  justify-content: center;
}

.checkbox-group.checkbox-week-days > div:not(:last-child) {
  margin-right: 15px;
}

.checkbox-group.checkbox-week-days label,
.checkbox-group.checkbox-week-days input {
  display: block;
  text-align: center;
  margin: 0 auto;
}

.container {
  display: flex;
  flex-direction: row;
  width: 100%;
  height: 100%;
}

.sidebar {
  background-color: #ddd;
}

.preview {
  flex: 1;
  background-color: #f1f1f1;
}
</style>

