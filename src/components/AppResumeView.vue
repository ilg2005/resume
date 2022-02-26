<template>
  <div class="card card-w70">
    <div v-if="!isBlank">
      <component :is="`app-${type}`" :text="text"></component>
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
  props: ['type', 'text'],
  data() {
    return {
      isBlank: true
    }
  }
}
</script>

<style scoped>

</style>
