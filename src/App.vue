<template>
  <div id="app" class="container">
  <SearchBar @termChange="onTermChange"/>
    <VideoList :videos="videos"></VideoList>
  </div>
</template>

<script>
import axios from 'axios';

import SearchBar from "@/components/SearchBar";
import VideoList from "@/components/VideoList";

export default {
  name: 'App',
  components: {
    VideoList,
    SearchBar
  },
  data(){
    return {
      api_key: process.env.API_KEY,
      videos: [],
    }
  },
  methods:{
    onTermChange: function (searchTerm){
      //get a request to youtube api
      axios.get("https://www.googleapis.com/youtube/v3/search", {
        params:{
          key: 'AIzaSyByvL8joeAty2_aWns4abQ980kvgWTQnVk',
          type: 'video',
          part: 'snippet',
          q: searchTerm
        }
      }).then(response => {
        this.videos = response.data.items}) //it takes some time so we use then

    }
  }
}
</script>

