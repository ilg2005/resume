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
import AppTitle from "@/components/ResumeViewTitle";
import AppSubtitle from "@/components/ResumeViewSubtitle";
import AppAvatar from "@/components/ResumeViewAvatar";
import AppText from "@/components/ResumeViewText";

export default {
  name: "AppResumeView",
  components: {AppTitle, AppSubtitle, AppAvatar, AppText},
  props: {
    fields: {
      type: Array,
      required: true
    }
  },
}
</script>

