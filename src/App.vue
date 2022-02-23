<template>
  <div class="container column">

    <app-form></app-form>

    <app-resume-view></app-resume-view>

  </div>
  <div class="container">
    <p v-if="!isCommentsLoaded">
      <button class="btn primary">Загрузить комментарии</button>
    </p>

    <app-loader v-else-if="isLoading"></app-loader>

    <app-comments v-else></app-comments>
  </div>

</template>

<script>
import AppForm from "@/components/AppForm";
import AppResumeView from "@/components/AppResumeView";
import AppComments from "@/components/AppComments";
import AppLoader from "@/components/AppLoader";

export default {
  components: {AppForm, AppResumeView, AppComments, AppLoader},

  data() {
    return {
      isLoading: false,
      isCommentsLoaded: false
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
