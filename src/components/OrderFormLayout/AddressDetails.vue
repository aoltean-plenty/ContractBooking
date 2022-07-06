<template>
  <div class="col-md-12">
    <h2 class="secondary-title">Address</h2>
  </div>

  <div
    :class="[
      {
        'col-md-12': 'default-grid',
        'form-group--error': v$.addressLine.$error,
      },
    ]"
  >
    <BaseInput
      label="Address line 1"
      type="text"
      id="inputAddress"
      v-model="addressLine"
    />
    <ErrorMessage
      v-if="v$.addressLine.$error"
      v-text="v$.addressLine.$errors[0].$message"
    />
  </div>

  <div class="col-md-12">
    <BaseInput
      label="Address line 2"
      type="text"
      id="inputAddress2"
      v-model="addressLine2"
    />
  </div>

  <div class="col-md-12">
    <BaseInput
      label="Address line 3"
      type="text"
      id="inputAddress3"
      v-model="addressLine3"
    />
  </div>

  <div
    :class="[
      { 'col-md-3': 'default-grid', 'form-group--error': v$.postCode.$error },
    ]"
  >
    <BaseInput label="Postcode" type="text" id="inputPlz" v-model="postCode" />
    <ErrorMessage
      v-if="v$.postCode.$error"
      v-text="v$.postCode.$errors[0].$message"
    />
  </div>

  <div
    :class="[
      { 'col-md-9': 'default-grid', 'form-group--error': v$.town.$error },
    ]"
  >
    <BaseInput label="Town" type="text" id="inputCity" v-model="town" />
    <ErrorMessage v-if="v$.town.$error" v-text="v$.town.$errors[0].$message" />
  </div>
</template>

<script>
import BaseInput from "../Inputs/BaseInput.vue";
import SelectField from "../Inputs/SelectField.vue";
import ErrorMessage from "../Errors/ErrorMessage.vue";
import useVuelidate from "@vuelidate/core";
import { required } from "@vuelidate/validators";

export default {
  name: "AddressDetails",
  components: { BaseInput, SelectField, ErrorMessage },

  data() {
    return {
      v$: useVuelidate(),
      addressLine: "",
      addressLine2: "",
      addressLine3: "",
      postCode: "",
      town: "",
    };
  },

  validations() {
    return {
      addressLine: { required },
      postCode: { required },
      town: { required },
    };
  },
};
</script>

<style scoped></style>
