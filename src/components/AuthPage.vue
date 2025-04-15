<template>
  <div>
    <login-form v-if="isLogin" @switchForm="toggleForm" @login="handleLogin" />
    <register-form v-else @switchForm="toggleForm" @register="handleRegister" />
  </div>
</template>

<script>
import LoginForm from './LoginForm.vue';
import RegisterForm from './RegisterForm.vue';

export default {
  name: 'AuthPage',
  components: {
    LoginForm,
    RegisterForm
  },
  data() {
    return {
      isLogin: false // ← Empieza mostrando el registro
    };
  },
  methods: {
    toggleForm() {
      this.isLogin = !this.isLogin;
    },
    handleLogin() {
      console.log('Logging in...');
      this.$emit('login-success'); // ← Avisamos a App.vue que se inició sesión
    },
    handleRegister() {
      console.log('Registering...');
      this.isLogin = true; // ← Volver al login luego del registro
    }
  }
};
</script>

<style scoped>
div {
  display: flex;
  justify-content: center;
  align-items: center;
  min-height: 100vh;
  background-color: #f9f9f9;
}
</style>
