<template>
  <div class="col-md-12">
    <h2 class="secondary-title">Payment Method</h2>
  </div>

  <div class="col-md-12">
    <div class="buttons-contain">
      <Button
        type="button"
        @click="triggerActiveDebit"
        button-text="Direct Debit"
        :class="[
          { btn: 'btn', 'btn-payment': 'payment', active: isDebitActive },
        ]"
      />
      <Button
        type="button"
        @click="triggerActiveInvoice"
        button-text="Invoice"
        :class="[
          { btn: 'btn', 'btn-payment': 'payment', active: isInvoiceActive },
        ]"
      />
    </div>
  </div>

  <div v-if="isDebitActive" class="payment-container">
    <div
      :class="[
        {
          'col-md-12': 'default-grid',
          'form-group--error': v$.accountOwner.$error,
        },
      ]"
    >
      <BaseInput
        label="Account Owner"
        type="text"
        id="accountName"
        v-model="accountOwner"
      />
      <ErrorMessage
        v-if="v$.accountOwner.$error"
        v-text="v$.accountOwner.$errors[0].$message"
      />
    </div>

    <div
      :class="[
        {
          'col-md-12': 'default-grid',
          'form-group--error': v$.accountNumber.$error,
        },
      ]"
    >
      <BaseInput
        label="Account Number"
        type="text"
        id="accountNumberInput"
        v-model="accountNumber"
      />
      <ErrorMessage
        v-if="v$.accountNumber.$error"
        v-text="v$.accountNumber.$errors[0].$message"
      />
    </div>

    <div
      :class="[
        {
          'col-md-12': 'default-grid',
          'form-group--error': v$.sortCode.$error,
        },
      ]"
    >
      <BaseInput
        label="Sort code"
        type="number"
        id="sortCodeInput"
        v-model="sortCode"
      />
      <ErrorMessage
        v-if="v$.sortCode.$error"
        v-text="v$.sortCode.$errors[0].$message"
      />
    </div>
  </div>

  <div v-if="isInvoiceActive" class="no-result">
    <p>No result here</p>
  </div>
</template>

<script>
import useVuelidate from "@vuelidate/core";
import { required } from "@vuelidate/validators";
import BaseInput from "../Inputs/BaseInput.vue";
import ErrorMessage from "../Errors/ErrorMessage.vue";
import Button from "../Buttons/Button.vue";
export default {
  name: "PaymentDetails.vue",

  components: {
    BaseInput,
    ErrorMessage,
    Button,
  },

  data() {
    return {
      v$: useVuelidate(),
      accountOwner: "",
      accountNumber: "",
      sortCode: "",
      isDebitActive: true,
      isInvoiceActive: false,
    };
  },

  validations() {
    return {
      accountOwner: { required },
      accountNumber: { required },
      sortCode: { required },
    };
  },

  methods: {
    triggerActiveDebit() {
      this.isDebitActive = !this.isDebitActive;
      this.isInvoiceActive = !this.isInvoiceActive;
    },

    triggerActiveInvoice() {
      this.isInvoiceActive = !this.isInvoiceActive;
      this.isDebitActive = !this.isDebitActive;
    },
  },
};
</script>

<style scoped>
.buttons-contain {
  margin-top: 7px;
  margin-bottom: 10px;
  text-align: right;
}

.buttons-contain button {
  margin: 0 3px;
}

.active {
  color: var(--plain-white);
  background-color: #04485b;
  outline: 0;
}

@media screen and (max-width: 499px) {
  .buttons-contain {
    margin-bottom: 10px;
    text-align: center;
  }
}
</style>
