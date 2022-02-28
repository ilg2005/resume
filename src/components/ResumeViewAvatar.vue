<template>
  <div class="avatar">
    <img :src= text>
  </div>
</template>

<script>
export default {
  name: "AppAvatar",
  props: {
    text: {
      type: String,
      required: true,
      validator(value) {
        return value.length > 3
      }
    }
  }}
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
