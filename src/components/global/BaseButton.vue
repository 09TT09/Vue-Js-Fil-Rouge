<template>
  <button class="button">
    {{ text }}
  </button>
</template>

<script>
export default {
  name: "base-button",
  props: ['text']
}
</script>

<style scoped>

.button{
  border: 0;
  width: 120px;
  height: 35px;
  color: black;
  background-color: white;
  transition: .25s;
  margin: 5px 0;
  border: solid crimson 1px;
}

.button:hover{
  transform: scale(1.1,1.1);
  background-color: crimson;
  color: white;
}

</style>