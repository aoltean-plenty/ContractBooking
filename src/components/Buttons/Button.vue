<template>
    <button :type="type" :class="btnClasses">{{ buttonText }}</button>
</template>

<script>
export default {
  name: "Button",

  props:{
    type:String,
    buttonText: String,
    btnClasses: Array
  },

}
</script>

<style scoped>

  div{
    text-align: right;
  }

</style>
