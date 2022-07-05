<template>
  <div class="col-md-12">
    <h2 class="secondary-title">Service Center Login Details</h2>
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
</template>

<script>
import useVuelidate from '@vuelidate/core'
import {email, minLength, required, sameAs} from '@vuelidate/validators'
import BaseInput from "../Inputs/BaseInput.vue";
import ErrorMessage from "../Errors/ErrorMessage.vue";

export default {
  name: "AccountDetails",
  components:{
    BaseInput,ErrorMessage
  },

  data(){
    return{
      v$: useVuelidate(),
      email:{
        email: '',
        repeat: '',
      },

      password:{
        password: '',
        repeat: '',
      },
    }
  },

  validations(){
    return{
      email:{
        email: {required,email},
        repeat: {required,email,sameAs: sameAs(this.email.email)},
      },
      password:{
        password: {required,minLength: minLength(8),},
        repeat: {required, sameAs: sameAs(this.password.password)},
      }
    }
  }

}
</script>

<style scoped>

</style>
