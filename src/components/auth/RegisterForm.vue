<template>
   <v-form fast-fail @submit.prevent="handleSubmit">
                <v-text-field
                  v-model="userName"
                  :rules="userNameRules"
                  label="Email"
                  variant="outlined"
                >
                </v-text-field>
                <v-text-field
                  v-model="password"
                  :rules="passwordRules"
                  label="Password"
                  :type="showPassword ? 'text' : 'password'"
                  variant="outlined"
                  :append-icon="showPassword ? 'mdi-eye' : 'mdi-eye-off'"
                  @click:append="showPassword = !showPassword"
                >
                </v-text-field>
                <v-btn
                  class="mt-2"
                  type="submit"
                  block
                  color="primary"
                  prepend-icon="mdi-login"
                >
                  Login
                </v-btn>
              </v-form>
</template>