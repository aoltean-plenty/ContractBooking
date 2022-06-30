<template>
  <header>
  </header>
  <main>
    <div class="row">
      <div class="col-md-10">
        <Form/>
      </div>
    </div>
  </main>
</template>

<script setup>
import Form from "./components/Form.vue";
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
