<template>
  <div>
    <h1>This is VideoList</h1>
    <ul>
      <VideoListItem v-for="video in videos" :key="video.etag" :video="video" 
      @select-video="selectedVideo" />
    </ul>
  </div>
</template>

<script>
import VideoListItem from '@/components/VideoListItem.vue'

export default {
  name: "VideoList",
  props: {
    videos: Array,
  },
  methods: {
    selectedVideo: function (video) {
      this.$emit('select-video', video)
    }
  },
  components: {
    VideoListItem,
  }
}
</script>


<style>

</style>