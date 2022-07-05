<template>
  <form @submit.prevent="submitForm">
    <div class="row">

    <ContactDetails/>
    <AddressDetails/>
    <PaymentDetails/>
    <AccountDetails/>

      <div class="col-md-12">
        <div class="btn-contain">
          <Button type="submit" button-text="Order" :class="[{'btn': 'btn', 'btn-submit': 'submit'}]"/>
        </div>
      </div>

    </div>
  </form>
</template>

<script>
import useVuelidate from '@vuelidate/core'
import Button from "./Buttons/Button.vue";
import ContactDetails from "./OrderFormLayout/ContactDetails.vue";
import AddressDetails from "./OrderFormLayout/AddressDetails.vue";
import PaymentDetails from "./OrderFormLayout/PaymentDetails.vue";
import AccountDetails from './OrderFormLayout/AccountDetails.vue';
import '@mdi/font/css/materialdesignicons.css';


export default {
  name: 'Form',
  components: {Button,ContactDetails,AddressDetails,PaymentDetails,AccountDetails},

  data(){
    return{
      v$: useVuelidate(),
    }
  },

  methods:{
     submitForm(){
      this.v$.$validate()
    },

  }
}

</script>

<style scoped>
.btn-contain{
  text-align: right;
}
</style>
