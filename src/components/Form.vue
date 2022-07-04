<template>
  <form @submit.prevent="submitForm">
    <div class="row">

      <div class="col-md-6">
        <BaseInput
            label="Company (optional)"
            type="text"
            id="inputCompany"
            v-model="company"/>
      </div>

      <div class="col-md-6">
      <BaseInput
          label="VAT number (optional)"
          type="text"
          id="inputVatNumber"
          v-model="vatNumber"/>
      </div>

      <div :class="[{'col-md-6': 'default-grid', 'form-group--error':v$.firstName.$error  }]">
        <BaseInput
            label="First Name"
            type="text"
            id="inputName2"
            :class="{ 'form-group--error': v$.firstName.$error }"
            v-model="firstName"/>
        <ErrorMessage v-if="v$.firstName.$error" v-text="v$.firstName.$errors[0].$message"/>
      </div>

      <div :class="[{'col-md-6': 'default-grid', 'form-group--error': v$.lastName.$error }]">
        <BaseInput
            label="Last Name"
            type="text"
            id="inputName3"
            v-model="lastName"/>
         <ErrorMessage v-if="v$.lastName.$error" v-text="v$.lastName.$errors[0].$message"/>
      </div>

      <div :class="[{'col-md-6': 'default-grid', 'form-group--error': v$.phone.$error }]">
      <BaseInput
          label="Phone"
          type="number"
          id="inputPhone"
          v-model="phone"/>
        <ErrorMessage v-if="v$.phone.$error" v-text="v$.phone.$errors[0].$message"/>
      </div>

      <SelectField @update:option="optionUpdate" label="Country"/>

    <div :class="[{'col-md-12': 'default-grid', 'form-group--error': v$.addressLine.$error }]">
      <BaseInput
          label="Address line 1"
          type="text"
          id="inputAddress"
          v-model="addressLine"/>
        <ErrorMessage v-if="v$.addressLine.$error" v-text="v$.addressLine.$errors[0].$message"/>
    </div>

    <div class="col-md-12">
      <BaseInput
          label="Address line 2"
          type="text"
          id="inputAddress2"
          v-model="addressLine2"/>
    </div>

    <div class="col-md-12">
      <BaseInput
          label="Address line 3"
          type="text"
          id="inputAddress3"
          v-model="addressLine3"/>
    </div>

      <div :class="[{'col-md-3': 'default-grid', 'form-group--error': v$.postCode.$error }]">
      <BaseInput
          label="Postcode"
          type="text"
          id="inputPlz"
          v-model="postCode"/>
         <ErrorMessage v-if="v$.postCode.$error" v-text="v$.postCode.$errors[0].$message"/>
      </div>

      <div :class="[{'col-md-9': 'default-grid', 'form-group--error': v$.town.$error }]">
      <BaseInput
          label="Town"
          type="text"
          id="inputCity"
          v-model="town"/>
         <ErrorMessage v-if="v$.town.$error" v-text="v$.town.$errors[0].$message"/>
      </div>

      <div :class="[{'col-md-6': 'default-grid', 'form-group--error': v$.email.$error }]">
      <BaseInput
          label="Email"
          type="email"
          id="inputEmail"
          v-model="email.email"/>
        <ErrorMessage v-if="v$.email.$error" v-text="v$.email.$errors[0].$message"/>
      </div>

      <div :class="[{'col-md-6': 'default-grid', 'form-group--error': v$.email.$error }]">
      <BaseInput
          class="col-md-6"
          label="Repeat Email"
          type="email"
          id="inputEmail2"
          v-model="email.repeat"/>
        <ErrorMessage v-if="v$.email.$error" v-text="v$.email.$errors[0].$message"/>
      </div>

      <div :class="[{'col-md-6': 'default-grid', 'form-group--error': v$.password.$error }]">
      <BaseInput
          label="Password"
          :type="showPassword ? 'text' : 'password'"
          :append-icon="showPassword ? 'mdi-eye' : 'mdi-eye-off'"
          @click:append="showPassword = !showPassword"
          id="inputPassword"
          v-model="password.password"/>
        <ErrorMessage v-if="v$.password.$error" v-text="v$.password.$errors[0].$message"/>
    </div>

      <div :class="[{'col-md-6': 'default-grid', 'form-group--error': v$.password.$error }]">
      <BaseInput
          label="Repeat Password"
          type="password"
          id="inputPassword2"
          v-model="password.repeat"/>
        <ErrorMessage v-if="v$.password.$error" v-text="v$.password.$errors[0].$message"/>
      </div>


      <div :class="[{'col-md-12': 'default-grid', 'form-group--error': v$.accountOwner.$error }]">
        <BaseInput
            label="Account Owner"
            type="text"
            id="accountName"
            v-model="accountOwner"/>
        <ErrorMessage v-if="v$.accountOwner.$error" v-text="v$.accountOwner.$errors[0].$message"/>
      </div>

      <div :class="[{'col-md-12': 'default-grid', 'form-group--error': v$.accountNumber.$error }]">
        <BaseInput
            label="Account Number"
            type="text"
            id="accountNumberInput"
            v-model="accountNumber"/>
        <ErrorMessage v-if="v$.accountNumber.$error" v-text="v$.accountNumber.$errors[0].$message"/>
      </div>

      <div :class="[{'col-md-12': 'default-grid', 'form-group--error': v$.sortCode.$error }]">
        <BaseInput
            label="Sort code"
            type="number"
            id="sortCodeInput"
            v-model="sortCode"/>
        <ErrorMessage v-if="v$.sortCode.$error" v-text="v$.sortCode.$errors[0].$message"/>
      </div>

      <BaseInput type="submit"/>

    </div>
  </form>
</template>

<script>
import useVuelidate from '@vuelidate/core'
import { required,email,minLength,sameAs } from '@vuelidate/validators'
import BaseInput from "./Inputs/BaseInput.vue";
import SelectField from "./Inputs/SelectField.vue";
import ErrorMessage from "./Errors/ErrorMessage.vue";
import '@mdi/font/css/materialdesignicons.css';

export default {
  name: 'Form',
  components: {BaseInput,SelectField,ErrorMessage},

  data(){
    return{
      v$: useVuelidate(),
      showPassword: false,
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
      },

      accountOwner:'',
      accountNumber: '',
      sortCode: '',
    }
  },

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
        password: {required,minLength: minLength(8),},
        repeat: {required, sameAs: sameAs(this.password.password)},
      },
      accountOwner: {required},
      accountNumber: {required},
      sortCode: {required},
    }
  },

  methods:{
    optionUpdate(value){
      this.country = value;
    },

     submitForm(){
      this.v$.$validate()
    },

  }
}

</script>

<style scoped>

</style>
