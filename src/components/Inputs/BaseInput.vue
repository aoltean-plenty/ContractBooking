<template>
  <label
    ><small>{{ label }}</small></label
  >
  <input
    :type="type"
    class="form-control"
    :value="modelValue"
    @input="$emit('update:modelValue', $event.target.value)"
    :id="id"
  />
</template>

<script>
export default {
  name: "BaseInput",
  props: {
    id: String,
    label: String,
    type: String,
    value: String,

    modelValue: {
      type: [String, Number],
      default: "",
    },
  },
};
</script>

<style scoped>

input:focus {
  outline: none;
  border-color: var(--fade-blue);
  background-color: var(--plain-white);
  box-shadow: none;
}

.form-group--error input {
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
input[type="number"] {
  -moz-appearance: textfield;
}
</style>
