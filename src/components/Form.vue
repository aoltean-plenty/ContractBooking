<template>
  <form @submit.prevent="submitForm">
    <div class="row">
      <BaseInput
          class="col-lg-6"
          label="Company (optional)"
          type="text"
          id="inputCompany"
          v-model="company"/>
      <BaseInput
          class="col-lg-6"
          label="VAT number (optional)"
          type="text"
          id="inputVatNumber"
          v-model="vatNumber"/>
      <BaseInput
          class="col-lg-6"
          label="First Name"
          type="text"
          id="inputName2"
          v-model="firstName"/>
      <span v-if="v$.lastName.$error">{{v$.lastName.$errors[0].$message}}</span>
      <BaseInput
          class="col-lg-6"
          label="Last Name"
          type="text"
          id="inputName3"
          v-model="lastName"/>
      <span v-if="v$.lastName.$error">{{v$.lastName.$errors[0].$message}}</span>
      <BaseInput
          class="col-lg-6"
          label="Phone"
          type="number"
          id="inputPhone"
          v-model="phone"/>

      <SelectField @update:option="optionUpdate" label="Country"/>

      <BaseInput
          class="col-lg-12"
          label="Address line 1"
          type="text"
          id="inputAddress"
          v-model="addressLine"/>
      <BaseInput
          class="col-lg-12"
          label="Address line 2"
          type="text"
          id="inputAddress2"
          v-model="addressLine2"/>
      <BaseInput
          class="col-lg-12"
          label="Address line 3"
          type="text"
          id="inputAddress3"
          v-model="addressLine3"/>
      <BaseInput
          class="col-md-3"
          label="Postcode"
          type="text"
          id="inputPlz"
          v-model="postCode"/>
      <BaseInput
          class="col-md-9"
          label="Town"
          type="text"
          id="inputCity"
          v-model="town"/>
      <BaseInput
          class="col-md-6"
          label="Email"
          type="email"
          id="inputEmail"
          v-model="email.email"/>
      <BaseInput
          class="col-md-6"
          label="Repeat Email"
          type="email"
          id="inputEmail2"
          v-model="email.repeat"/>
      <BaseInput
          class="col-md-6"
          label="Password"
          type="password"
          id="inputPassword"
          v-model="password.password"/>
      <span v-if="v$.password.$error">{{v$.password.$errors[0].$message}}</span>
      <BaseInput
          class="col-md-6"
          label="Repeat Password"
          type="password"
          id="inputPassword2"
          v-model="password.repeat"/>
      <BaseInput type="submit"/>
    </div>
  </form>
</template>

<script>
import useVuelidate from '@vuelidate/core'
import { required,email,minLength,sameAs } from '@vuelidate/validators'
import BaseInput from "./BaseInput.vue";
import SelectField from "./SelectField.vue";


export default {
  name: 'Form',
  components: {BaseInput,SelectField},

  data(){
    return{
      v$: useVuelidate(),
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

  // setup() {
  //   return{ v$: useVuelidate()}
  // },

  validations (){
    return{
      firstName:{required},
      lastName: {required},
      phone:{required},
      addressLine: {required},
      postCode: {required},
      town: {required},
      email:{
        email: {required,email},
        repeat: {required,email,sameAs: sameAs(this.email.email)},
      },

      password:{
        password: {required,minLength: minLength(8)},
        repeat: {required, sameAs: sameAs(this.password.password)},
      }
    }
  },

  methods:{
    optionUpdate(value){
      this.country = value;
    },

     submitForm(){
      this.v$.$validate()
      if(!this.v$.$error){
        alert('Form Submitted');
      } else{
        alert('Form did not pass validation');
      }
    }
  }

}

</script>

<style scoped>



</style>
