<template>
  <div>
    <input @input="onInput">
  </div>
</template>

<script>
export default {
  name: "SearchBar",
  methods: {
    onInput(event){
      //emitting events to the app component
      this.$emit('termChange', event.target.value);
    }
  }
}
</script>

<style scoped>

</style>