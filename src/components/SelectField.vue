<template>
  <div class="col-md-6">
    <label>{{ label }}</label>
    <select class="form-control">
      <option value="1">Australia</option>
      <option value="2">Uk</option>
    </select>
  </div>
</template>

<script>
export default {
  name: "SelectField",

  props:{
    label: String,
  }
}
</script>

<style scoped>
label{
  line-height: 1;
}

select{
  margin-bottom: 10px;
  padding: 6px 13px 6px 13px;
  border-color: var(--light-grey);
  outline: none;
}

select:focus{
  outline: none;
  border-color:var(--light-grey);
  box-shadow: none;
}
</style>
