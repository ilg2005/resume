<template>
  <p v-if="!isCommentsLoaded">
    <button class="btn primary" @click="$emit('loading')">Загрузить комментарии</button>
  </p>

  <div class="card" v-else>
    <h2>Комментарии</h2>
    <ul class="list">
      <li class="list-item"
          v-for="comment in comments"
          :key="comment.id"
      >
        <div>
          <p><strong>{{ comment.email }}</strong></p>
          <small>{{ comment.body }}</small>
        </div>
      </li>
    </ul>
  </div>

</template>

<script>
export default {
  name: "AppComments",
  emits: ['loading'],
  props: {
    isCommentsLoaded: Boolean,
    comments: {
      type: Array,
      required: false
    },
  },

}
</script>
