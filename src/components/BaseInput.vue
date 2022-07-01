<template>
    <label><small>{{label}}</small></label>
    <input
        :type="type"
        class="form-control"
        :value="modelValue"
        @input="$emit('update:modelValue', $event.target.value)"
        :id="id"/>
</template>

<script>
  export default {
    name: 'BaseInput',
    props:{
      id: String,
      label:String,
      type:String,
      value:String,

      modelValue:{
        type: [String,Number],
        default: ''
      }
    },

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

input{
  padding:16px 24px;
  box-sizing: border-box;
  border:1px solid var(--border-grey);
  background-color: var(--plain-white);
  outline: none;
  border-radius: 5px;
  height: 56px;
  transition: 0.25s ease-in-out;
}

input:hover{
  background-color: var(--background-grey);
}

input:focus{
  outline: none;
  border-color:var(--fade-blue);
  background-color: var(--plain-white);
  box-shadow: none;
}

.form-group--error input{
  border-color: var(--red);
}

/*** Remove arrows for number input ***/

/* Chrome, Safari, Edge, Opera */
input::-webkit-outer-spin-button,
input::-webkit-inner-spin-button {
  -webkit-appearance: none;
  margin: 0;
}

/* Firefox */
input[type=number] {
  -moz-appearance: textfield;
}

</style>
