<template>
  <div class="col-md-6">
    <label><small>{{ label }}</small></label>
    <select class="form-control" v-model="selectedOption" @change="optionChanged">
      <option value="1">Australia</option>
      <option value="2">Uk</option>
    </select>
  </div>
</template>

<script>
export default {
  name: "SelectField",

  data(){
    return{
      selectedOption: null
    }
  },

  props:{
    label: String,
  },

  methods:{
    optionChanged(value){
       this.$emit('update:option',this.selectedOption) ;
    }
  }
}
</script>

<style scoped>

label{
  font-family: 'Source Sans Pro', sans-serif;
  font-style: normal;
  font-weight: var(--weight-bold);
  font-size: var(--medium-size);
  line-height: var(--medium-line);
  letter-spacing: var(--small-space);
  color: var(--dark-grey);
}
select{
  margin-bottom: 10px;
  padding: 16px 24px;
  gap: 8px;
  border: 1px solid var(--border-grey);
  border-radius: 5px;
  outline: none;
  height: 56px;
}

select:focus{
  outline: none;
  border-color:var(--border-grey);
  box-shadow: none;
}
</style>
