<template>
  <div>
    <div v-if="selectedVideo">
    <iframe :src="videoURI"></iframe>
    <h1>{{ selectedVideo.snippet.title | unescape }}</h1>
    <p>{{ selectedVideo.snippet.description | unescape }}</p>
    </div>
  </div>
</template>

<script>
import _ from "lodash"

export default {
  name: "VideoDetail",

  props: {
    selectedVideo: Object,
  },
  computed: {
    videoURI: function() {
      const videoId = this.selectedVideo.id.videoId
      return `https://www.youtube.com/embed/${videoId}`
    }
  },
  filters: {
      unescape: function (text) {
        return _.unescape(text)
      },
  }
}
</script>

<style>

</style>