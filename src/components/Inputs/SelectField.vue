<template>
  <div class="col-md-6">
    <label
      ><small>{{ label }}</small></label
    >
    <div class="country-select">
      <select
        class="form-control"
        v-model="selectedOption"
        @change="optionChanged"
      >
        <option value="1">Australia</option>
        <option value="2">Uk</option>
      </select>
      <span class="arrow-contain"><i class="fa-solid fa-angle-down"></i></span>
    </div>
  </div>
</template>

<script>
export default {
  name: "SelectField",

  data() {
    return {
      selectedOption: null,
    };
  },

  props: {
    label: String,
  },

  methods: {
    optionChanged(value) {
      this.$emit("update:option", this.selectedOption);
    },
  },
};
</script>

<style scoped>
select:focus {
  outline: none;
  border-color: var(--border-grey);
  box-shadow: none;
}

.country-select {
  position: relative;
}

.arrow-contain {
  position: absolute;
  top: 30%;
  right: 10px;
}
</style>
