<template>
  <h2>{{ text }}</h2>
</template>

<script>
export default {
  name: "AppSubtitle",
  props: {
    text: {
      type: String,
      required: true,
      validator(value) {
        return value.length > 3
      }
    }
  }
}
</script>
