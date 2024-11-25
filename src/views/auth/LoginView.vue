<script setup>
import { ref } from 'vue';
import { useRouter } from 'vue-router';
import AppLayout from '@/components/layout/AppLayout.vue';

const passwordVisible = ref(false);
const email = ref('');
const password = ref('');
const router = useRouter();

const togglePasswordVisibility = () => {
  passwordVisible.value = !passwordVisible.value;
};

const login = () => {
  if (email.value && password.value) {
    alert(`Login attempt with:\nEmail: ${email.value}\nPassword: ${password.value}`);
    // Add login logic here (e.g., API call)
  } else {
    alert('Please fill in both email and password.');
  }
};

const navigateToRegister = () => {
  router.push('/register'); // Update this route according to your app
};
</script>

<template>
  <AppLayout>
    <template #content>
      <v-row class="d-flex justify-center">
        <v-col cols="12" md="6" class="mx-auto">
          <v-card class="glass-card border-thin pa-4">
            <v-card-title class="text-h5 text-center">Login</v-card-title>
            <v-card-text>
              <v-form>
                <v-text-field
                  v-model="email"
                  label="Email"
                  type="email"
                  placeholder="Enter your email"
                  required
                  class="mb-4"
                ></v-text-field>
                <v-text-field
                  v-model="password"
                  :type="passwordVisible ? 'text' : 'password'"
                  label="Password"
                  placeholder="Enter your password"
                  required
                  append-icon="mdi-eye"
                  @click:append="togglePasswordVisibility"
                  class="mb-4"
                ></v-text-field>
                <v-btn
                  color="primary"
                  block
                  @click="login"
                  class="mb-2"
                >
                  Login
                </v-btn>
              </v-form>
              <div class="text-center">
                <v-btn
                  text
                  color="primary"
                  @click="navigateToRegister"
                >
                  Click here to register
                </v-btn>
              </div>
            </v-card-text>
          </v-card>
        </v-col>
      </v-row>
    </template>
  </AppLayout>
</template>
