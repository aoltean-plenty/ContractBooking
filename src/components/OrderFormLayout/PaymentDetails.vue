<template>

  <div class="col-md-12">
    <h2 class="secondary-title">Payment Method</h2>
  </div>

  <div class="col-md-12">
    <div class="btn-contain">
      <Button type="button" button-text="Direct Debit" :class="[{'btn': 'btn', 'btn-payment': 'payment'}]"/>
      <Button type="button"  button-text="Invoice" :class="[{'btn': 'btn', 'btn-payment': 'payment'}]"/>
    </div>
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
</template>

<script>

import useVuelidate from '@vuelidate/core'
import { required} from '@vuelidate/validators'
import BaseInput from "../Inputs/BaseInput.vue";
import ErrorMessage from "../Errors/ErrorMessage.vue";
import Button from "../Buttons/Button.vue";
export default {
  name: "PaymentDetails.vue",

  components:{
    BaseInput,
    ErrorMessage,
    Button
  },

  data(){
    return{
      v$: useVuelidate(),
      accountOwner:'',
      accountNumber: '',
      sortCode: '',
    }
  },

  validations(){
    return{
      accountOwner: {required},
      accountNumber: {required},
      sortCode: {required}
    }
  }
}
</script>

<style scoped>
.btn-contain{
  margin-top: 7px;
  text-align: right;
}

.btn-contain button{
  margin: 0 3px;
}

@media screen and (max-width: 499px){
  .btn-contain{
    margin-bottom: 10px;
    text-align: center;
  }
}

</style>
