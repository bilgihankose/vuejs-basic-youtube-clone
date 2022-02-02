<template>
  <div id="app">
  <SearchBar @termChange="onTermChange"/>
  </div>
</template>

<script>
import axios from 'axios';

import SearchBar from "@/components/SearchBar";
const API_KEY = 'AIzaSyCXI4IQ5tPxE0Ttllk4srTUnTG7ra8Y9rs';

export default {
  name: 'App',
  components: {
    SearchBar
  },
  methods:{
    onTermChange: function (searchTerm){
      //get a request to youtube api
      axios.get("https://www.googleapis.com/youtube/v3/search", {
        params:{
          key: API_KEY,
          type: 'video',
          part: 'snippet',
          q: searchTerm
        }
      }).then(response => console.log(response)) //it takes some time so we use then

    }
  }
}
</script>

