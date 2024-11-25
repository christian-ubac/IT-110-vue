<script setup>
import { ref } from 'vue';
import { useRouter } from 'vue-router';
import AppLayout from '@/components/layout/AppLayout.vue';
import { useDisplay } from 'vuetify';

const showPassword = ref(false);
const fullName = ref('');
const email = ref('');
const password = ref('');
const confirmPassword = ref('');

const fullNameRules = [v => !!v || 'Full Name is required'];
const emailRules = [
  v => !!v || 'Email is required',
  v => /.+@.+\..+/.test(v) || 'Email must be valid',
];
const passwordRules = [
  v => !!v || 'Password is required',
  v => (v && v.length >= 6) || 'Password must be at least 6 characters',
];
const confirmPasswordRules = [
  v => !!v || 'Confirmation is required',
  v => v === password.value || 'Passwords must match',
];

const { mobile } = useDisplay();
const router = useRouter();

const handleRegister = () => {
  if (fullName.value && email.value && password.value && confirmPassword.value) {
    if (password.value !== confirmPassword.value) {
      alert('Passwords do not match.');
      return;
    }
    console.log('Registered with:', fullName.value, email.value);
    alert('Registration successful! Redirecting to login...');
    router.push('/login'); // Redirect to login after successful registration
  } else {
    alert('Please fill out all fields correctly.');
  }
};
</script>

<template>
  <AppLayout>
    <template #content>
      <v-row>
        <v-col cols="12" md="6" class="mx-auto pt-16">
          <v-card class="mx-auto" elevation="24">
            <v-card-title class="text-center">
              <v-img
                class="mx-auto"
                src="/public/images/agri2.jpg"
                :width="mobile ? '75' : '25%'"
              ></v-img>
              <h3 class="font-weight-black text-center">AgriHub</h3>
              <p class="font-weight-bold">Register Form</p>
            </v-card-title>
            <v-card-text class="bg-surface-light pt-4">
              <v-form>
                <v-text-field
                  v-model="fullName"
                  label="Full Name"
                  :rules="fullNameRules"
                  required
                  class="mb-4"
                ></v-text-field>
                <v-text-field
                  v-model="email"
                  label="Email"
                  type="email"
                  :rules="emailRules"
                  required
                  class="mb-4"
                ></v-text-field>
                <v-text-field
                  v-model="password"
                  :type="showPassword ? 'text' : 'password'"
                  label="Password"
                  :rules="passwordRules"
                  required
                  append-icon="mdi-eye"
                  @click:append="showPassword = !showPassword"
                  class="mb-4"
                ></v-text-field>
                <v-text-field
                  v-model="confirmPassword"
                  :type="showPassword ? 'text' : 'password'"
                  label="Confirm Password"
                  :rules="confirmPasswordRules"
                  required
                  append-icon="mdi-eye"
                  @click:append="showPassword = !showPassword"
                  class="mb-4"
                ></v-text-field>
                <v-btn
                  color="primary"
                  block
                  @click="handleRegister"
                  class="mb-2"
                >
                  Register
                </v-btn>
              </v-form>
              <v-divider class="my-5"></v-divider>
              <h5 class="text-center">
                Already have an account?
                <RouterLink class="text-primary" to="/login"
                  >Click here to Login</RouterLink
                >
              </h5>
            </v-card-text>
          </v-card>
        </v-col>
      </v-row>
    </template>
  </AppLayout>
</template>
