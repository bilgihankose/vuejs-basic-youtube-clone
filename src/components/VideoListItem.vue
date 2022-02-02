<template>
<li class="list-group-item" @click="onVideoSelect">
  <div class="row">
    <img class="mr-3" :src="tumbnailUrl" alt="">
    <div class="media-body">
      <h6 class="mt-0">{{ video.snippet.title }}</h6>
    </div>
  </div>
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
  },
  methods: {
    onVideoSelect() {
      this.$emit('videoSelect', this.video);
    }
  }
}
</script>
<style>
li{
  display: flex;
  cursor: pointer;
}

li:hover{
  transition: box-shadow .3s;
  box-shadow: 0 0 11px rgba(33,33,33,.2);
  background: #eee;

}
</style>

