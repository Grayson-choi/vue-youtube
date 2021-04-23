<template>
  <div id="app">
    <SearchBar @send-search="inputSearch" />
    <VideoList :videos="videos" @select-video="onSelectedVideo"/>
    <VideoDetail :selectedVideo="selectedVideo" />
  </div>
</template>

<script>
import SearchBar from '@/components/SearchBar.vue'
import VideoList from '@/components/VideoList.vue'
import VideoDetail from '@/components/VideoDetail.vue'
import axios from 'axios'

const API_KEY = process.env.VUE_APP_YOUTUBE_API_KEY
const API_URL = 'https://www.googleapis.com/youtube/v3/search'

export default {
  name: 'App',
  components: {
    SearchBar,
    VideoList,
    VideoDetail,
  },
  data: function () {
    return {
      videos: [],
      selectedVideo: {},
    }
  },
  methods: {
    inputSearch: function (searchData) {
      console.log(API_KEY)
      axios.get(API_URL, {params: {
        key: API_KEY,
        part: 'snippet',
        q: searchData,
      }}).then(res => {
        this.videos = res.data.items
      }).catch(err => {
        console.error(err)
      })
    },
    onSelectedVideo: function (video) {
      this.selectedVideo = video
    }

  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
