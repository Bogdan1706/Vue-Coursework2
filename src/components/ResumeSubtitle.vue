<template lang="">
   <h2>{{newSubtitle}}</h2>
</template>
<script>
export default {
  props: {
     subtitle: {
      type: String,
      required: true,
      default: '',
    }
  },
  data () {
    return {
      newSubtitle: this.subtitle
    }
  }
}
</script>
<style lang="">

</style>
