<script setup>
import { ref } from 'vue'
import AppLayout from '@/components/layout/AppLayout.vue'
import RegisterForm from '@/components/auth/Registration.vue'
import { useDisplay } from 'vuetify'

const showPassword = ref(false)
const userName = ref('')
const password = ref('')

const userNameRules = [v => !!v || 'Name is required']
const passwordRules = [v => !!v || 'Password is required']
const { mobile } = useDisplay()

const handleSubmit = () => {
  if (userName.value && password.value) {
    // Handle login logic here
    console.log('Logged in with:', userName.value, password.value)
  }
}
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
              <p class="font-weight-bold">Login Form</p>
            </v-card-title>
            <v-card-text class="bg-surface-light pt-4">
              <v-divider class="my-5"></v-divider>
             <RegistrationForm>
              
             </RegistrationForm>
              <v-divider class="my-5"></v-divider>
              <h5 class="text-center">
                Don't have an account?
                <RouterLink class="text-primary" to="/register"
                  >Click here to Register</RouterLink
                >
              </h5>
            </v-card-text>
          </v-card>
        </v-col>
      </v-row>
    </template>
  </AppLayout>
</template>
