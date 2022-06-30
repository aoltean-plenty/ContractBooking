<template>
  <div :class="column">
    <label><small>{{label}}</small></label>
    <input @input="updateValue($event.target.value)" :type="type" class="form-control" :value="value" :id="id"/>
  </div>
</template>

<script>
  export default {
    name: 'BaseInput',
    props:{
      id: String,
      label:String,
      column:String,
      type:String,
      value:String
    },

  }
</script>

<style scoped>

label{
  line-height: 1;
}

input{
  margin-bottom: 10px;
  padding: 6px 13px 6px 13px;
  border-color: var(--light-grey);
  outline: none;
}

input:focus{
  outline: none;
  border-color:var(--light-grey);
  box-shadow: none;
}
</style>
