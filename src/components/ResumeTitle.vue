<template lang="">
  <h1>{{ newTitle }}</h1>
</template>
<script>
export default {
  props: {
    title: {
      type: String,
      required: true,
      default: ''
    }
  },
  data() {
    return {
      newTitle: this.title,
    }
  }
}
</script>
<style lang=""></style>
