<template>
  <p>
    {{ text }}
  </p>
</template>

<script>
export default {
  name: "AppText",
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
