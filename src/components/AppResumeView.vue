<template>
  <div class="card card-w70">
    <div v-if="fields.length">
      <component v-for="field in fields"
                 :key="field"
                 :is="`app-${field.type}`"
                 :text="field.text"
      ></component>
    </div>
    <h3 v-else>Добавьте первый блок, чтобы увидеть результат</h3>
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
  props: ['fields'],
  data() {
    return {

    }
  }
}
</script>

<style scoped>

</style>
