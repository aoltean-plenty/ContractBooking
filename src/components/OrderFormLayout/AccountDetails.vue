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

  <div :class="[{'col-md-6': 'default-grid', 'form-group--error': v$.password.$error , 'password': 'hasPassword'}]">
    <BaseInput
        label="Password"
        id="inputPassword"
        :type="passwordState ? 'password' : 'text'"
        v-model="password.password"/>
     <i @click="showPassword" :class="passwordState ? 'fa-solid fa-eye-slash' : 'fa-solid fa-eye'"></i>
    <ErrorMessage v-if="v$.password.$error" v-text="v$.password.$errors[0].$message"/>
  </div>

  <div :class="[{'col-md-6': 'default-grid', 'form-group--error': v$.password.$error, 'password': 'hasPassword' }]">
    <BaseInput
        label="Repeat Password"
        id="inputPassword2"
        :type="passwordState ? 'password' : 'text'"
        v-model="password.repeat"/>
    <i @click="showPassword" :class="passwordState ? 'fa-solid fa-eye-slash' : 'fa-solid fa-eye'"></i>
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
      passwordState: true,
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

  methods:{
    showPassword(){
      this.passwordState = !this.passwordState;
    },
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


.password{
  position: relative;
}

.password i{
  position: absolute;
  right: 0;
  bottom: 29.5px;
  padding: 0 20px 0 0;
  cursor: pointer;
  color: var(--dark-grey);
}

</style>
