<template>
  <v-form class="px-3 pb-3" fast-fail @submit.prevent="() => {}">
    <v-text-field
      v-model="userName"
      label="Email"
      variant="outlined"
    ></v-text-field>
    <v-text-field
      v-model="password"
      :type="passwordVisible ? 'text' : 'password'"
      label="Password"
      variant="outlined"
    >
      <template #append>
        <v-icon @click="togglePasswordVisibility">
          {{ passwordVisible ? 'mdi-eye-off' : 'mdi-eye' }}
        </v-icon>
      </template>
    </v-text-field>
    <v-btn
      block
      variant="outlined"
      rounded="xl"
      size="x-large"
      class="mt-2 mx-auto d-flex mb-5"
      type="submit"
      color="primary"
      prepend-icon="mdi-login"
    >
      Login
    </v-btn>
    <v-divider class="my-5"></v-divider>
    <p class="text-center mt-3">Forgot Password?</p>
    <br />
    <p class="text-center">
      Don't have an account?
      <router-link to="/register" class="text-primary"> Login </router-link>
    </p>
    <br />
  </v-form>
</template>
