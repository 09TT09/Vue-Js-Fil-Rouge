<template>

  <div class="selection_cours_card">
    <h3 :class="isTypeCours" class="banniere">{{ selectionunique.nom }}</h3>
    <p>date: {{ selectionunique.date }} - {{ selectionunique.heure }}</p>
    <base-button
      v-if="buttonClicked"
      text="Retirer"
      @click="addToSelection"
    >
    </base-button>
  </div>

</template>

<script>

export default {
  name: "selection-card",
  props: ['selectionunique'],
  data() {
    return {
      buttonClicked: true
    }
  },
  computed: {
    typeCours() {
      if(this.selectionunique.type == "matiere scientifique"){
        return 0
      }
      else if(this.selectionunique.type == "langue"){
        return 1
      }
      else if(this.selectionunique.type == "autre"){
        return 2
      }
      return 3
    },
    isTypeCours() {
      return { 
        'banniere_ms': this.typeCours == 0,
        'banniere_langue': this.typeCours == 1,
        'banniere_autre': this.typeCours == 2,
        'banniere_vide': this.typeCours == 3,
      }
    }
  },
  methods: {
    addToSelection() {
      this.$emit('delete-cours', this.selectionunique)
    }
  }
}
</script>

<style scoped>

.selection_cours_card{
  margin: 10px 10px;
  width: 20%;
  min-width: 230px;
  max-width: 300px;
  border-radius: 3px;
  color: white;
  border: solid crimson 2px;
  background-color: #333131;
  text-align: center;
}

.banniere{
  margin: 0;
  padding: 10px 0;
}

.banniere_ms{background-color: crimson;}
.banniere_langue{background-color: #71009c;}
.banniere_autre{background-color: #ef9a00;}
.banniere_vide{background-color: white; color: black;}


</style>