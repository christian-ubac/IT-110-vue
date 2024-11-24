<script setup>
import { ref } from 'vue'
import AppLayout from '@/components/layout/AppLayout.vue'
import LoginForm from '@component/auth/LoginForm.vue'
import { useDisplay } from 'vuetify'

const passwordVisible = ref(false)
const userName = ref('')
const password = ref('')

const togglePasswordVisibility = () => {
  passwordVisible.value = !passwordVisible.value
  const { mobile } = useDisplay()

}
</script>

<template>
  <AppLayout>
    <template #content>
      <v-row class="d-flex justify-center">
        <v-col cols="12" md="6" class="mx-auto">
          <v-card class="glass-card border-thin">
            <LoginForm></LoginForm>
           
          </v-card>
        </v-col>
      </v-row>
    </template>
  </AppLayout>
</template>
