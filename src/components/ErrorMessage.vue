<template>
  <span class="error-message"></span>
</template>

<script>
export default {
  name: "ErrorMessage",
}
</script>

<style scoped>
.error-message{
  font-family: 'Source Sans Pro', sans-serif;
  font-style: normal;
  font-weight: var(--weight-medium);
  font-size: var(--small-size);
  line-height: var(--small-line);
  letter-spacing: var(--small-space);
  color:var(--red);
}
</style>
