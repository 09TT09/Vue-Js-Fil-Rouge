<template>

  <div class="cours_card">
    <div class="center">
      <h3 :class="isTypeCours" class="banniere">{{ cours.nom }}</h3>
      <p>Place: {{ cours.place }} | Prix: {{ cours.prix }}</p>
      <p>Statut: <span :class="isCoursPlein">{{ cours.statut }}</span></p>
      <p>Date: {{ cours.date }} - {{ cours.heure }}</p>
      <base-button
        v-if="buttonClicked"
        text="Sélectionner"
        @click="addToSelection"
      >
      </base-button>
      <p v-else class="p_else">Cours sélectionné</p>
    </div>
  </div>

</template>

<script>
export default {
  name: "cours-card",
  props: ['cours'],
  data() {
    return {
      buttonClicked: true
    }
  },
  computed: {
    coursPlein() {
      if(this.cours.statut == "plein"){
        return 0
      }
      else if(this.cours.statut == "quelques place restantes"){
        return 1
      }
      return 2
    },
    typeCours() {
      if(this.cours.type == "matiere scientifique"){
        return 0
      }
      else if(this.cours.type == "langue"){
        return 1
      }
      else if(this.cours.type == "autre"){
        return 2
      }
      return 3
    },
    isCoursPlein() {
      return { 
        'cours_card_plein': this.coursPlein == 0,
        'cours_card_libre': this.coursPlein == 1, 
        'cours_card_vide': this.coursPlein == 2
      }
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
      this.$emit('add-cours', this.cours)
      this.buttonClicked = false
    }
  }
}
</script>

<style scoped>

.cours_card{
  margin: 10px 10px;
  text-decoration: none;
  list-style:none;
  width: 20%;
  min-width: 230px;
  max-width: 300px;
  border-radius: 3px;
  color: white;
  border: solid crimson 2px;
  background-color: #333131;
}

.banniere{
  margin: 0;
  padding: 10px 0;
}

.banniere_ms{background-color: crimson;}
.banniere_langue{background-color: #71009c;}
.banniere_autre{background-color: #ef9a00;}
.banniere_vide{background-color: white; color: black;}

.center{
  text-align: center;
}

.cours_card_vide{color: lime;}
.cours_card_libre{color: yellow;}
.cours_card_plein{color: red;}

.p_else{
  height: 40px;
  line-height: 35px;
  margin: 5px 0;
  color: lime;
}

</style>