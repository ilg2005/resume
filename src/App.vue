<template>
  <div class="container column">

    <app-form></app-form>

    <app-resume-view></app-resume-view>

  </div>
  <div class="container">
    <p v-if="!isCommentsLoaded">
      <button class="btn primary" @click="loadComments">Загрузить комментарии</button>
    </p>
    <app-comments v-else :comments="this.comments"></app-comments>
    <app-loader v-if="isLoading"></app-loader>
  </div>

</template>

<script>
import AppForm from "@/components/AppForm";
import AppResumeView from "@/components/AppResumeView";
import AppComments from "@/components/AppComments";
import AppLoader from "@/components/AppLoader";
import axios from "axios"

export default {
  components: {AppForm, AppResumeView, AppComments, AppLoader},

  data() {
    return {
      isLoading: false,
      isCommentsLoaded: false,
      comments: [],
    }
  },

  methods: {
    loadComments() {
      this.isLoading = true

      setTimeout(async () => {
        try {
          const {data} = await axios.get('https://jsonplaceholder.typicode.com/comments?_limit=42')

          this.comments = data
          console.log(this.comments)

          this.isLoading = false
          this.isCommentsLoaded = true
        } catch (e) {
          this.isLoading = false
          console.log(e.message)
        }
      }, 1500)


    }
  }

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
