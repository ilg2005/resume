<template>
  <app-alert
      v-if="this.alert"
      :alert="this.alert"
      @close="this.alert = null"
  ></app-alert>

  <div class="container column">
    <app-form
        @submitted="collectSubmittedData"
        @alert="(obj) => { this.alert = obj }"
    ></app-form>
    <app-resume-view :fields="submittedData"></app-resume-view>
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
import AppAlert from "@/components/AppAlert";
import axios from "axios"

export default {
  components: {AppForm, AppResumeView, AppComments, AppLoader, AppAlert},

  data() {
    return {
      isLoading: false,
      isCommentsLoaded: false,
      comments: [],
      alert: null,
      submittedData: []
    }
  },

  mounted() {
    this.loadFields()
  },

  methods: {
    collectSubmittedData(obj) {
      this.submittedData.push(obj)
    },

    async loadComments() {
      this.isLoading = true

      try {
        const {data} = await axios.get('https://jsonplaceholder.typicode.com/comments?_limit=42')

        if (!data) {
          this.alert = {
            type: 'warning',
            title: 'Пока комментариев нет',
            text: ''
          }
        }
        this.comments = data
        this.isLoading = false
        this.isCommentsLoaded = true
      } catch (e) {
        this.isLoading = false
        this.alert = {
          type: 'danger',
          title: 'Комментарии не были загружены',
          text: e.message
        }
      }
    },

    async loadFields() {
      this.isLoading = true

      try {
        const {data} = await axios.get('https://vue-demo-deploy-7673c-default-rtdb.asia-southeast1.firebasedatabase.app/fields.json')

        if (!data) {
          this.isLoading = false
          console.warn('Данных в базе пока нет')
          return false
        }

        this.submittedData = Object.keys(data).map(key => ({
          id: key,
          ...data[key]
        }))

        this.isLoading = false
      } catch (e) {
        this.isLoading = false
        this.alert = {
          type: 'danger',
          title: 'Данные не были загружены',
          text: e.message
        }
      }
    }
  }

}
</script>

