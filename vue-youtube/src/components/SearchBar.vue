<template>
  <div>
    <input type="text" v-model="inputData" @keypress.enter="onInputKeyword">
  </div>
  
</template>

<script>

export default {
  name: 'SearchBar',
  data: function() {
    return {
      inputData: '',
    }
  },
  methods: {
    onInputKeyword: function () {
      this.$emit('send-search', this.inputData)
    }
  }
}
</script>

<style>

</style>