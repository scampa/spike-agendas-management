<template>
  <ul id="myUL">
    <!-- <li v-for="rule in rules" :key="rule.name">{{ rule.name }}</li> -->
    <li v-for="rule in rules" :key="rule.name">
        <span class="caret"><b>{{ rule.name }}</b> - {{ rule.type }} - {{ rule.weekDays }} - {{ rule.dateFrom }} - 
        {{ rule.dateTo }} - {{ rule.timeFrom }} - {{ rule.timeTo }} - {{ rule.groupByRule }}</span>
    </li>
  </ul>
</template>

<script>
export default {
  name: 'TreeView',
  props: {
    rules: Array,
    treeDict: Object
  }
}

</script>


<style>
 /* Remove default bullets */
ul, #myUL {
  list-style-type: none;
}

/* Remove margins and padding from the parent ul */
#myUL {
  margin: 0;
  padding: 0;
}

/* Style the caret/arrow */
.caret {
  cursor: pointer;
  user-select: none; /* Prevent text selection */
}

/* Create the caret/arrow with a unicode, and style it */
.caret::before {
  content: "\25B6";
  color: black;
  display: inline-block;
  margin-right: 6px;
  margin-left: 16px;
}

/* Rotate the caret/arrow icon when clicked on (using JavaScript) */
.caret-down::before {
  transform: rotate(90deg);
}

/* Hide the nested list */
.nested {
  display: none;
}

/* Show the nested list when the user clicks on the caret/arrow (with JavaScript) */
.active {
  display: block;
} 
</style>