<template lang="">
  <p>
    {{ newText }}
  </p>
</template>
<script>
export default {
  props: {
     text: {
      type: String,
      required: true,
      default: '',
    }
  },
  data () {
    return {
      newText: this.text
    }
  }
}
</script>
<style lang="">

</style>
