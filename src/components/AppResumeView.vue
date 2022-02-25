<template>
  <div class="card card-w70">
    <div v-if="!isBlank">
      <app-title></app-title>
      <app-avatar></app-avatar>
      <app-subtitle></app-subtitle>
      <app-text></app-text>
    </div>
    <h3 v-if="isBlank">Добавьте первый блок, чтобы увидеть результат</h3>
  </div>

</template>

<script>
import AppTitle from "@/components/AppTitle";
import AppSubtitle from "@/components/AppSubtitle";
import AppAvatar from "@/components/AppAvatar";
import AppText from "@/components/AppText";

export default {
  name: "AppResumeView",
  components: {AppTitle, AppSubtitle, AppAvatar, AppText},
  data() {
    return {
      isBlank: true
    }
  }
}
</script>

<style scoped>

</style>
