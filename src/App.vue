<!-- src/App.vue -->
<template>
  <div class="min-h-screen bg-black text-green-500 font-mono">
    <LoginScreen v-if="!isLoggedIn" @login-success="handleLoginSuccess" />
    <BMWViewer v-else />
  </div>
</template>

<script setup>
import { ref } from 'vue';
import LoginScreen from './components/LoginScreen.vue';
import BMWViewer from './components/BMWViewer.vue';

const isLoggedIn = ref(false);

const handleLoginSuccess = () => {
  isLoggedIn.value = true;
};
</script>