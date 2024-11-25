<script setup>
import { ref } from 'vue';
import { useRouter } from 'vue-router';

const user = ref({ name: '', isLoggedIn: false });
const router = useRouter();

const handleLogout = () => {
  user.value.isLoggedIn = false;
  user.value.name = '';
  alert('You have logged out.');
  router.push('/login'); // Redirect to login page
};
</script>

<template>
  <v-container>
    <v-row class="d-flex justify-center">
      <v-col cols="12" md="8" class="text-center pt-16">
        <v-card elevation="10" class="py-5 px-4">
          <v-card-title>
            <h2>Welcome to AgriHub!</h2>
          </v-card-title>
          <v-card-text>
            <p v-if="user.isLoggedIn">Hello, {{ user.name }}! You are now logged in.</p>
            <p v-else>Please log in or register to access more features.</p>
          </v-card-text>
          <v-btn color="primary" @click="router.push('/dashboard')" class="my-2">
            Go to Dashboard
          </v-btn>
          <v-btn color="error" @click="handleLogout" v-if="user.isLoggedIn">
            Logout
          </v-btn>
        </v-card>
      </v-col>
    </v-row>
  </v-container>
</template>
