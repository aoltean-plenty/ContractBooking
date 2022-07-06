<template>
  <button :type="type" :class="btnClasses">
    {{ buttonText }} <i v-show="iconTrigger" :class="iconClasses"></i>
  </button>
</template>

<script>
export default {
  name: "Button",

  props: {
    type: String,
    buttonText: String,
    btnClasses: Array,
    iconClasses: String,
    iconTrigger: Boolean,
  },
};
</script>

<style scoped>
div {
  text-align: right;
}
</style>
