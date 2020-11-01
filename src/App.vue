<template>
  <nav-bar
    @change-component="updateSelectedComponent"
  ></nav-bar>

  <keep-alive>
    <component 
      :is="selectedComponent"
      v-bind="currentProps"
      @update-selection="updateSelection"
      @delete-selection="deleteSelection"
    >
    </component>
  </keep-alive>
</template>

<script>

import CoursList from './components/CoursList.vue'
import SelectionList from './components/SelectionList.vue'
import NavBar from './components/navigation/NavBar.vue'

export default {
  name: 'App',
  components: {
    CoursList,
    NavBar,
    SelectionList
  },
  data() {
    return {
      selectedComponent: 'cours-list',
      selectionArray: []
    }
  },
  computed: {
    currentProps() {
      if(this.selectedComponent == "selection-list") {
        return { selection: this.selectionArray }
      }
      return false
    }
  },
  methods: {
    updateSelectedComponent(comp) {
      this.selectedComponent = comp
    },
    updateSelection(cours) {
      this.selectionArray.push(cours)
    },
    deleteSelection(selectionunique) {
      let x = this.selectionArray.indexOf(selectionunique)
      this.selectionArray.splice(x, 1)
    }
  }
}
</script>

<style>
body {
  margin: 0;
}
</style>
