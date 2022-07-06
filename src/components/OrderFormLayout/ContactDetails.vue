<template>
  <div class="col-md-12">
    <h2 class="secondary-title">Please let us know your contact details</h2>
  </div>

  <div class="col-md-6">
    <BaseInput
      label="Company (optional)"
      type="text"
      id="inputCompany"
      v-model="company"
    />
  </div>

  <div class="col-md-6">
    <BaseInput
      label="VAT number (optional)"
      type="text"
      id="inputVatNumber"
      v-model="vatNumber"
    />
  </div>

  <div
    :class="[
      { 'col-md-6': 'default-grid', 'form-group--error': v$.firstName.$error },
    ]"
  >
    <BaseInput
      label="First Name"
      type="text"
      id="inputName2"
      :class="{ 'form-group--error': v$.firstName.$error }"
      v-model="firstName"
    />
    <ErrorMessage
      v-if="v$.firstName.$error"
      v-text="v$.firstName.$errors[0].$message"
    />
  </div>

  <div
    :class="[
      { 'col-md-6': 'default-grid', 'form-group--error': v$.lastName.$error },
    ]"
  >
    <BaseInput
      label="Last Name"
      type="text"
      id="inputName3"
      v-model="lastName"
    />
    <ErrorMessage
      v-if="v$.lastName.$error"
      v-text="v$.lastName.$errors[0].$message"
    />
  </div>

  <div
    :class="[
      { 'col-md-6': 'default-grid', 'form-group--error': v$.phone.$error },
    ]"
  >
    <BaseInput label="Phone" type="number" id="inputPhone" v-model="phone" />
    <ErrorMessage
      v-if="v$.phone.$error"
      v-text="v$.phone.$errors[0].$message"
    />
  </div>
  <SelectField @update:option="optionUpdate" label="Country" />
</template>

<script>
import useVuelidate from "@vuelidate/core";
import { required } from "@vuelidate/validators";
import BaseInput from "../Inputs/BaseInput.vue";
import SelectField from "../Inputs/SelectField.vue";
import ErrorMessage from "../Errors/ErrorMessage.vue";

export default {
  name: "ContactDetails",
  components: { BaseInput, SelectField, ErrorMessage },

  data() {
    return {
      v$: useVuelidate(),
      company: "",
      vatNumber: "",
      firstName: "",
      lastName: "",
      phone: "",
      country: "",
    };
  },

  validations() {
    return {
      firstName: { required },
      lastName: { required },
      phone: { required },
    };
  },

  methods: {
    optionUpdate(value) {
      this.country = value;
    },
  },
};
</script>

<style scoped></style>
