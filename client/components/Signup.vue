<template>
  <v-card>
    <v-form ref="form" v-model="valid" lazy-validation="true">
      <v-text-field v-model="firstName" :rules="nameRules" label="Given Name" required />
      <v-text-field v-model="lastName" :rules="nameRules" label="Family Name" required />

      <v-text-field v-model="email" :rules="emailRules" label="E-mail" required />

      <v-text-field
        v-model="password"
        :append-icon="show1 ? 'mdi-eye' : 'mdi-eye-off'"
        :rules="[rules.required, rules.min]"
        :type="show1 ? 'text' : 'password'"
        name="input-10-1"
        label="Password"
        hint="At least 8 characters"
        counter
        @click:append="show1 = !show1"
      />
      <v-text-field
        v-model="password"
        :append-icon="show1 ? 'mdi-eye' : 'mdi-eye-off'"
        :rules="[rules.required, rules.min]"
        :type="show1 ? 'text' : 'password'"
        name="input-10-1"
        label="Confirm Password"
        hint="At least 8 characters"
        counter
        @click:append="show1 = !show1"
      />
      <v-btn :disabled="!valid" color="success" class="mr-4" @click="sumbitSignup">Submit</v-btn>
    </v-form>
  </v-card>
</template>

<script lang="ts">
import {
  CognitoUserAttribute,
  CognitoUserPool,
  ISignUpResult,
  NodeCallback
} from 'amazon-cognito-identity-js'

const poolData = {
  UserPoolId: '', // Your user pool id here
  ClientId: '' // Your client id here
}

const userPool = new CognitoUserPool(poolData)
const attributeList: CognitoUserAttribute[] = []
const validationData: CognitoUserAttribute[] = []

const signupCallback: NodeCallback<Error | undefined, ISignUpResult> = (
  err: Error,
  result: ISignUpResult
): void => {
  if (err) {
    alert(err.message || JSON.stringify(err))
    return
  }

  const cognitoUser = result.user
  console.log("user name is " + cognitoUser.getUsername())
}

export default {
  data: () => ({
    valid: true,
    firstName: '',
    lastName: '',
    nameRules: [
      v => !!v || 'Name is required'
    ],
    email: '',
    emailRules: [
      v => !!v || 'E-mail is required',
      v => /.+@.+\..+/.test(v) || 'E-mail must be valid',
    ],
  }),
  methods: {
    sumbitSignup () {
      userPool.signUp(
        this.$data.email,
        'password',
        attributeList,
        validationData,
        signupCallback
      )
    }
  }
}
</script>

<style>
</style>
