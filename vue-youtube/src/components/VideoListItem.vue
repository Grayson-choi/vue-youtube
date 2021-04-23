<template>
  <div>
    <h1>This is VideoListItem</h1>
    <li v-if="video" @click="selectVideo">
      <img :src="imgSrc" alt="youtube-thumbnail-image">
      {{ video.snippet.title | unescape }}
    </li>
  </div>
</template>

<script>
import _ from 'lodash'

export default {
  name: 'VideoListItem',
  props: {
    video: Object,
  },
  methods: {
    selectVideo: function () {
      this.$emit('select-video', this.video)
    }
  },
  computed: {
    imgSrc: function () {
      return this.video.snippet.thumbnails.default.url
    }
  },
    filters: {
      unescape: function (text) {
        return _.unescape(text)
      }
    },
}
</script>

<style>

</style>