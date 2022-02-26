<template>
  <h1>{{ text }}</h1>
</template>

<script>
export default {
  name: "AppTitle",
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
