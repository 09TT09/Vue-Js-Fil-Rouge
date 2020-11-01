<template>
  <div class="selection_box">Vous
    <span v-if="nbrCours">avez sélectionné {{ selection.length }} cours</span>
    <span v-else>n'avez pas sélectionné de cours</span>
  </div>
</template>

<script>
export default {
  name: "selection-box",
  props: ['selection'],
  computed: {
    nbrCours() {
      if(this.selection.length > 0){
        return true
      }
      return false
    }
  }
}
</script>

<style scoped>

.selection_box{
  text-align: center;
}

</style>