<template>https://github.com/NotSeijas/reto-2.git
  <div class="app-container">
    <!-- Mostrar AuthPage si no ha iniciado sesión -->
    <AuthPage v-if="!isLoggedIn" @login-success="handleLoginSuccess" />

    <!-- Mostrar la app principal si ya inició sesión -->
    <div v-else>
      <Header />
      <div class="main-content">
        <SideBar />
        <TaskList />
      </div>
      <Footer />
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue';
import Header from './components/Header.vue';
import Footer from './components/Footer.vue';
import SideBar from './components/SideBar.vue';
import TaskList from './components/TaskList.vue';
import AuthPage from './components/AuthPage.vue';

const isLoggedIn = ref(false);

function handleLoginSuccess() {
  isLoggedIn.value = true;
}
</script>

<style scoped>
.app-container {
  display: flex;
  flex-direction: column;
  height: 100vh;
}

.main-content {
  display: flex;
  flex: 1;
}
</style>
