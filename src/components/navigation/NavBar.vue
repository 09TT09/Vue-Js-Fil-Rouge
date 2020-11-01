<template>
  <div class="navbar">

    <button
      class="button"
      v-for="(link, index) in navigation"
      :key="index"
      @click="selectComponent(link.component)" 
    >
      {{ link.name }}
    </button>
    
  </div>
</template>

<script>
export default {
  name: "nav-bar",
  data() {
    return {
      navigation: [
        { name: "Liste des cours", component: "cours-list" },
        { name: "Cours sélectionnés", component: "selection-list" }
      ]
    }
  },
  methods: {
    selectComponent(comp) {
      this.$emit('change-component', comp)
    }
  }
}
</script>

<style scoped>

.navbar{
  height: 60px;
  width: 100%;
  background-color: #202020;
  border-bottom: solid crimson 2px;
  text-align: center;
  line-height: 60px;
}

.button{
  width: 150px;
  height: 35px;
  margin: 0 5px;
  transition: .25s;
  border: 0;
}

.button:hover{
  transform: scale(1.1,1.1);
  background-color: crimson;
}

</style>