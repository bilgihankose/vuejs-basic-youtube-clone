<template>
<li class="list-group-item mb-1">
  <img :src="tumbnailUrl" alt="">
  {{ video.snippet.title }}
</li>
</template>

<script>
export default {
  name: "VideoListItem",
  props: ["video"],
  computed:{
    tumbnailUrl(){
      return this.video.snippet.thumbnails.default.url
    }
  }
}
</script>
<style>
li{
  cursor: pointer;
}

li:hover{
  transition: box-shadow .3s;
  box-shadow: 0 0 11px rgba(33,33,33,.2);

}
</style>

