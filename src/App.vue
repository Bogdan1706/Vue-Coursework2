<template>
  <div class="container column">
    <app-form
      @create="createBlocks"
    ></app-form>
    <div class="card card-w70">
      <app-resume
        :blocks="blocks"
      ></app-resume>
    </div>
  </div>
  <div class="container">
    <p>
      <button class="btn primary"
        v-if="btnActive"
        @click="load"
      >Загрузить комментарии</button>
    </p>
    <app-loader
      v-if="loading"
    ></app-loader>
    <app-comments
      v-else-if="this.comments.length !== 0"
      :comments="comments"
    ></app-comments>
  </div>
</template>

<script>
import AppForm from './components/AppForm.vue'
import AppResume from './components/AppResume.vue'
import AppComments from './components/AppComments.vue'
import AppLoader from './components/AppLoader.vue'
import axios from 'axios'
export default {
  data () {
    return {
      blocks: [],
      comments: [],
      loading: false,
      btnActive: true
    }
  },
  methods: {
    async createBlocks () {
      const {data} = await axios.get('https://resume-generation-ac32b-default-rtdb.europe-west1.firebasedatabase.app/resume.json')
      this.blocks = Object.keys(data).map( key => {
        return {
          id: key,
           ...data[key]
        }
      })
    },

    async load () {
      this.btnActive = false
      this.loading = true
      const { data } = await axios.get('https://jsonplaceholder.typicode.com/comments?_limit=42')
      setTimeout (() => {
         this.comments = Object.keys(data).map( key => {
        return {
          id: key,
           ...data[key]
          // body: data[key].body,
          // email: data[key].email,
        }
      })
      this.loading = false
      }, 2000)
     
    }
  },
  components: {
    AppForm,
    AppResume,
    AppComments,
    AppLoader
  },
}
</script>

<style>
  .avatar {
    display: flex;
    justify-content: center;
  }

  .avatar img {
    width: 150px;
    height: auto;
    border-radius: 50%;
  }
</style>
