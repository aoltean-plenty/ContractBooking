<template>
  <header>
  </header>
  <main>
    <div class="container">
      <div class="mx-auto">
        <FormOrder/>
      </div>
    </div>

  </main>
</template>

<script setup>
import FormOrder from "./components/FormOrder.vue";

</script>

<style>
@import './assets/base.css';

#app {
  max-width: 1280px;
  margin: 0 auto;
  padding: 2rem;
  font-weight: normal;
}

header {
  line-height: 1.5;
}
</style>
