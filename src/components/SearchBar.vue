<template>
  <div>
    <!--added event modifier because API has limited request-->
    <input type="text" placeholder="Search" @keyup.enter="onInput">
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
input{
  width: 75%;
}

div{
  text-align: center;
  margin: 20px;
}
</style>