<template>
  <div id="app">
  <SearchBar @termChange="onTermChange"/>
  </div>
</template>

<script>
import SearchBar from "@/components/SearchBar";
const API_KEY = 'AIzaSyCXI4IQ5tPxE0Ttllk4srTUnTG7ra8Y9rs';

export default {
  name: 'App',
  components: {
    SearchBar
  },
  methods:{
    onTermChange: function (searchTerm){
    console.log(searchTerm)
    }
  }
}
</script>

