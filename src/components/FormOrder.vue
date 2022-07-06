<template>
  <form @submit.prevent="submitForm">
    <div class="row">
      <ContactDetails />
      <AddressDetails />
      <PaymentDetails />
      <AccountDetails />

      <div class="col-md-12">
        <div class="buttons-contain">
          <Button
            type="submit"
            button-text="Order"
            :iconTrigger="true"
            icon-classes="fa-solid fa-arrow-right"
            :class="[{ btn: 'btn', 'btn-submit': 'submit' }]"
          />
        </div>
      </div>
    </div>
  </form>
</template>

<script>
import useVuelidate from "@vuelidate/core";
import Button from "./Buttons/Button.vue";
import ContactDetails from "./OrderFormLayout/ContactDetails.vue";
import AddressDetails from "./OrderFormLayout/AddressDetails.vue";
import PaymentDetails from "./OrderFormLayout/PaymentDetails.vue";
import AccountDetails from "./OrderFormLayout/AccountDetails.vue";

export default {
  name: "FormOrder",
  components: {
    Button,
    ContactDetails,
    AddressDetails,
    PaymentDetails,
    AccountDetails,
  },

  data() {
    return {
      v$: useVuelidate(),
    };
  },

  methods: {
    submitForm() {
      this.v$.$validate();
    },
  },
};
</script>

<style scoped>
.buttons-contain {
  margin-top: 20px;
  text-align: right;
}
</style>
