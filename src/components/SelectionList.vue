<template>

  <div class="center">
    <h1>Cours sélectionnés</h1>
    <selection-box 
      :selection="selection"
    >
    </selection-box>
  </div>

  <div class="flex_box">
    <selection-card
      v-for="(selectionunique, index) in selection"
      :key="index"
      :selectionunique="selectionunique"
      @delete-cours="deleteCoursToSelection"
    >
    </selection-card>
  </div>

</template>

<script>
import SelectionBox from './SelectionBox.vue'
import SelectionCard from './SelectionCard.vue'

export default {
  name: "selection-list",
  props: ['selection'],
  components: {
    SelectionCard,
    SelectionBox
  },
  methods: {
    deleteCoursToSelection(selectionunique) {
      this.$emit('delete-selection', selectionunique)
    }
  }
}
</script>

<style scoped>

.center{
  text-align: center;
}

.flex_box{
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
}

</style>