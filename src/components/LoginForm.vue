<template>
  <div class="form-wrapper">
    <div class="form-card">
      <h2>Iniciar Sesión</h2>
      <form>
        <label>Usuario:</label>
        <input type="text" v-model="username" />

        <label>Contraseña:</label>
        <input type="password" v-model="password" />

        <label>Tipo de Usuario:</label>
        <select v-model="userType">
          <option>Usuario</option>
          <option>Administrador</option>
        </select>

        <button type="button" @click="login">Entrar</button>
      </form>
      <p class="switch-text">¿No tienes cuenta?
        <a href="#" @click.prevent="$emit('switchForm')">Regístrate</a>
      </p>
    </div>
  </div>
</template>

<script>
export default {
  name: 'LoginForm',
  data() {
    return {
      username: '',
      password: '',
      userType: 'Usuario'
    };
  },
  methods: {
    login() {
      this.$emit('login');
    }
  }
};
</script>

<style scoped>
.form-wrapper {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
  background: #f1f3f5;
}

.form-card {
  background: #fff;
  padding: 2rem;
  border-radius: 12px;
  box-shadow: 0 8px 20px rgba(0, 0, 0, 0.1);
  width: 350px;
}

h2 {
  text-align: center;
  margin-bottom: 1.5rem;
}

label {
  font-weight: 600;
  display: block;
  margin-top: 1rem;
}

input,
select {
  width: 100%;
  padding: 0.6rem;
  border: 1px solid #ccc;
  border-radius: 8px;
  margin-top: 0.3rem;
  outline: none;
}

button {
  margin-top: 1.5rem;
  width: 100%;
  padding: 0.7rem;
  background-color: #4f46e5;
  color: white;
  border: none;
  border-radius: 8px;
  cursor: pointer;
  font-weight: bold;
  transition: background 0.3s;
}

button:hover {
  background-color: #4338ca;
}

.switch-text {
  margin-top: 1rem;
  text-align: center;
  font-size: 0.9rem;
}

.switch-text a {
  color: #4f46e5;
  text-decoration: none;
  font-weight: bold;
}
</style>
