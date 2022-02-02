<template>
  <div id="app">
  <SearchBar @termChange="onTermChange"/>
  </div>
</template>

<script>
import axios from 'axios';

import SearchBar from "@/components/SearchBar";

export default {
  name: 'App',
  components: {
    SearchBar
  },
  data(){
    return {
      api_key: process.env.API_KEY
    }
  },
  methods:{
    onTermChange: function (searchTerm){
      //get a request to youtube api
      axios.get("https://www.googleapis.com/youtube/v3/search", {
        params:{
          key: this.api_key,
          type: 'video',
          part: 'snippet',
          q: searchTerm
        }
      }).then(response => console.log(response)) //it takes some time so we use then

    }
  }
}
</script>

