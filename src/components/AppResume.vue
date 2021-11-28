<template lang="">
  <resume-base v-if="blocks.length === 0"></resume-base>
  <div v-for="block in blocks" :key="block.id">
    <div v-if="block.typeBlock === 'title'">
      <!-- <resume-title
            :title="block.text"
          ></resume-title> -->
      <component :is="resumeTitle" :title="block.text"></component>
    </div>
    <div v-if="block.typeBlock === 'subtitle'">
      <!-- <resume-subtitle
            :subtitle="block.text"
          ></resume-subtitle> -->
      <component :is="resumeSubtitle" :subtitle="block.text"></component>
    </div>
    <div v-if="block.typeBlock === 'avatar'">
      <!-- <resume-avatar
            :avatar="block.text"
          ></resume-avatar> -->
      <component :is="resumeAvatar" :avatar="block.text"></component>
    </div>
    <div v-if="block.typeBlock === 'text'">
      <!-- <resume-text
            :text="block.text"
        ></resume-text> -->
      <component :is="resumeText" :text="block.text"></component>
    </div>
  </div>
</template>
<script>
import ResumeBase from "./ResumeBase.vue";
import ResumeTitle from "./ResumeTitle.vue";
import ResumeSubtitle from "./ResumeSubtitle.vue";
import ResumeAvatar from "./ResumeAvatar.vue";
import ResumeText from "./ResumeText.vue";
export default {
  props: {
    blocks: {
      type: Array,
      required: true,
      default: Array,
      validator: function (value) {
        if (!value) {
          return false;
        }
        return true;
      },
    },
  },
  computed: {
    resumeTitle() {
      return "resume-title";
    },
    resumeSubtitle() {
      return "resume-subtitle";
    },
    resumeAvatar() {
      return "resume-avatar";
    },
    resumeText() {
      return "resume-text";
    },
  },
  components: {
    ResumeBase,
    ResumeTitle,
    ResumeSubtitle,
    ResumeAvatar,
    ResumeText,
  },
};
</script>
<style lang=""></style>
