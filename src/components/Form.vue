<template>
  <form>
    <div class="row">
      <BaseInput class="col-lg-6" label="Company (optional)" type="text" id="inputCompany"/>
      <BaseInput class="col-lg-6" label="VAT number (optional)" type="text" id="inputVatNumber"/>
      <BaseInput class="col-lg-6" label="First Name" type="text" id="inputName2"/>
      <BaseInput class="col-lg-6" label="Last Name" type="text" id="inputName3"/>
      <BaseInput class="col-lg-6" label="Phone" type="number" id="inputPhone" />
      <SelectField label="Country"/>
      <BaseInput class="col-lg-12" label="Address line 1" type="text" id="inputAddress"/>
      <BaseInput class="col-lg-12" label="Address line 2" type="text" id="inputAddress2"/>
      <BaseInput class="col-lg-12" label="Address line 2" type="text" id="inputAddress3"/>
      <BaseInput class="col-md-3" label="Postcode" type="text" id="inputPlz"/>
      <BaseInput class="col-md-9" label="Town" type="text" id="inputCity"/>
      <BaseInput class="col-md-6" label="Email" type="email" id="inputEmail"/>
      <BaseInput class="col-md-6" label="Repeat Email" type="email"  id="inputEmail2"/>
      <BaseInput class="col-md-6" label="Password" type="password" id="inputPassword"/>
      <BaseInput class="col-md-6" label="Repeat Password" type="password" id="inputPassword2"/>
      <BaseInput type="submit"/>
    </div>
  </form>
</template>

<script>

import BaseInput from "./BaseInput.vue";
import SelectField from "./SelectField.vue";

export default {
  name: 'Form',
  components: {BaseInput,SelectField},

  data(){
    return{
      company:'',
      vatNumber:'',
      firstName: '',
      lastName: '',
      phone: '',
      country: '',
      addressLine:'',
      addressLine2: '',
      addressLine3: '',
      postCode: '',
      town: '',

      email:{
        email: '',
        repeat: '',
      },

      password:{
        password: '',
        repeat: '',
      }
    }
  },

  emits:['input']
}

</script>

<style scoped>

</style>
