<template>
  <form class="card card-w30" @submit.prevent="submitValue">
    <div class="form-control">
      <label for="type">Тип блока</label>
      <select id="type" v-model="submittedData.type">
        <option value="title">Заголовок</option>
        <option value="subtitle">Подзаголовок</option>
        <option value="avatar">Аватар</option>
        <option value="text">Текст</option>
      </select>
    </div>

    <div class="form-control">
      <label for="value">Значение</label>
      <textarea id="value" rows="3" v-model="submittedData.text"></textarea>
    </div>

    <button class="btn primary" :disabled="!isTextValid">Добавить</button>
  </form>

</template>

<script>
import axios from "axios";

export default {
  name: "AppForm",
  emits: {
    submitted: ({ type, text }) => {
      if (type && text) {
        return true
      } else {
        console.warn('Invalid submitted event payload!')
        return false
      }
    },
    alert: null
  },
  data() {
    return {
      submittedData: {
        type: 'title',
        text: ''
      },
    }
  },
  methods: {
    resetForm() {
      this.submittedData.type = 'title'
      this.submittedData.text = ''
    },

    submitValue() {
      this.$emit('submitted', {...this.submittedData})
      const sendPostRequest = async () => {
        try {
          const resp = await axios.post(process.env.VUE_APP_URL, this.submittedData);
          console.log(resp.data);
        } catch (e) {
          const alert = {
            type: 'danger',
            title: 'Данные не были загружены',
            text: e.message
          }
          this.$emit('alert',  {...alert})
        }
      };

      sendPostRequest();

      this.resetForm()
    }
  },
  computed: {
    isTextValid() {
      return this.submittedData.text.length > 3
    }
  }
}
</script>
