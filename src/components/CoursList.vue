<template>

  <h1 class="titre">Liste des {{ coursData.nom }}</h1>

  <selection-box 
    :selection="selection"
  >
  </selection-box>

  <div class="flex_box">
  <cours-card
    v-for="(cours, index) in coursData.allcours"
    :key="index"
    :cours="cours"
    @add-cours="addCoursToSelection"
  >
  </cours-card>
  </div>

</template>

<script>
import coursData from '../assets/data/cours.json'
import CoursCard from './CoursCard.vue'
import SelectionBox from './SelectionBox.vue'

export default {
  name: "cours-List",
  components: {
    CoursCard,
    SelectionBox
  },
  data() {
    return {
      coursData : coursData,
      selection: []
    }
  },
  methods: {
    addCoursToSelection(cours) {
      this.selection.push(cours)
      this.$emit('update-selection', cours)
    }
  }
}
</script>

<style scoped>

.flex_box{
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
}

.titre{
  text-align: center;
}

</style>