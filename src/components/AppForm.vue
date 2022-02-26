<template>
  <form class="card card-w30" @submit.prevent="submitValue">
    <div class="form-control">
      <label for="type">Тип блока</label>
      <select id="type">
        <option value="title">Заголовок</option>
        <option value="subtitle">Подзаголовок</option>
        <option value="avatar">Аватар</option>
        <option value="text">Текст</option>
      </select>
    </div>

    <div class="form-control">
      <label for="value">Значение</label>
      <textarea id="value" rows="3" v-model="submittedValue"></textarea>
    </div>

    <button class="btn primary" :disabled="!isTextValid">Добавить</button>
  </form>

</template>

<script>
export default {
  name: "AppForm",
  data() {
    return {
      submittedValue: '',
    }
  },
  methods: {
    submitValue() {
      console.log(this.submittedValue)
      this.submittedValue = ''
    }
  },
  computed: {
    isTextValid() {
     return  this.submittedValue.length > 3
    }
  }
}
</script>

<style scoped>

</style>
