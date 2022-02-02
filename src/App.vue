<template>
  <div id="app" class="container">
  <SearchBar @termChange="onTermChange"/>
    <div class="row">
      <VideoDetail :video="selectedVideo"></VideoDetail>
      <VideoList @videoSelect="onVideoSelect" :videos="videos" ></VideoList>
    </div>
  </div>
</template>

<script>
import axios from 'axios';

import SearchBar from "@/components/SearchBar";
import VideoList from "@/components/VideoList";
import VideoDetail from "@/components/VideoDetail";

export default {
  name: 'App',
  components: {
    VideoList,
    SearchBar,
    VideoDetail
  },
  data(){
    return {
      api_key: process.env.API_KEY,
      videos: [],
      selectedVideo: null
    }
  },
  methods:{
    onVideoSelect(video){
      this.selectedVideo = video
    },
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

