<template lang="">
  <form class="card card-w30" @submit.prevent="addNewBlock">
    <div class="form-control">
      <label for="type">Тип блока</label>
      <select id="type" v-model="block.typeBlock">
        <option value="title">Заголовок</option>
        <option value="subtitle">Подзаголовок</option>
        <option value="avatar">Аватар</option>
        <option value="text">Текст</option>
      </select>
    </div>

    <div class="form-control">
      <label for="value">Значение</label>
      <textarea id="value" rows="3" v-model="block.text"></textarea>
    </div>
    <button class="btn primary" :disabled="disabled" @click="createBlock">
      Добавить
    </button>
  </form>
</template>
<script>
export default {
  emits: {
    create: null,
  },
  data() {
    return {
      block: {
        typeBlock: "title",
        text: "",
      },
    };
  },
  // https://resume-generation-ac32b-default-rtdb.europe-west1.firebasedatabase.app/resume.json
  methods: {
    async createBlock() {
      const response = await fetch(
        'https://resume-generation-ac32b-default-rtdb.europe-west1.firebasedatabase.app/resume.json',
        {
          method: 'POST',
          headers: {
            "Content-Type": "application/json"
          },
          body: JSON.stringify({
            typeBlock: this.block.typeBlock,
            text: this.block.text
          }),
        }
      )
      const firebaseData = await response.json()
      console.log(firebaseData)
      this.$emit("create", this.block);
      this.block = {
        typeBlock: "title",
        text: "",
      };
    },
  },
  computed: {
    disabled() {
      if (this.block.text.length < 4) {
        return true;
      }
      return false;
    },
  },
};
</script>
<style lang=""></style>
