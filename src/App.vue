<template>
  <div class="background">
  <img src="../src/assets/wp.jpg" />
  </div>
    <h1>Ubah Password</h1>
    <div>
      <input type="password" v-model="password" @input="passwordsMatch" placeholder="Enter your password">
      <input type="password" v-model="confirmPassword" placeholder="Confirm your password">
      <button @click="verifyPassword">Verify Password</button>
      <p v-if="passwordsMatch" style="color: green;">Passwords match!</p>
      <p v-else  style="color: red;">Passwords do not match!</p>
    </div>
</template>

<script setup>
import { ref, computed } from 'vue';

const password = ref('');
const confirmPassword = ref('');

const passwordsMatch = computed(() => password.value === confirmPassword.value && password.value.length > 0);

const verifyPassword = () => {
  if (passwordsMatch.value) {
    // Passwords match, clear inputs
    password.value = '';
    confirmPassword.value = '';
  }
};

</script>

<style scoped>
.background img{
  position: fixed;
  top: 0;
  left: 0;
  min-height: 90%;
  min-width: 1500px;
  width: 100%;
  height: 100%;
  overflow: hidden;
  z-index: -2;
  object-fit: cover;
  -webkit-background-size:cover; -moz-background-size:cover; -o-background-size:cover; background-size: cover;
  filter: brightness(0.8);
}
input {
  display: flex;
  margin-left: 29%;
  margin-bottom: 5px;
  padding: 10px;
}
p{
  font-weight: bold;
  text-shadow: 0 0 10px white;
}
</style>
