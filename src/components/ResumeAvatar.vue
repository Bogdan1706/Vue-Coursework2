<template lang="">
    <div class="avatar">
        <img :src ="newAvatar">
      </div>
</template>
<script>
export default {
  props: {
    avatar: {
      type: String,
      required: true,
      default: '',
      validator: function (value) {
        if(~value.indexOf('https://')) {
          return true
        }
        return false
      }
    }
  },
  data () {
    return {
      src: '',
      newAvatar: this.avatar
    }
  }
}
</script>
<style lang="">

</style>
