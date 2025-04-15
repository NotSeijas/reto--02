<template>
  <div class="form-wrapper">
    <div class="form-card">
      <h2>Crear Cuenta</h2>
      <form>
        <label>Usuario:</label>
        <input type="text" v-model="username" />

        <label>Email:</label>
        <input type="email" v-model="email" />

        <label>Contraseña:</label>
        <input type="password" v-model="password" />

        <label>Confirmar Contraseña:</label>
        <input type="password" v-model="confirmPassword" />

        <label>Tipo de Usuario:</label>
        <select v-model="userType">
          <option>Usuario</option>
          <option>Administrador</option>
        </select>

        <button type="button" @click="register">Registrarse</button>
      </form>
      <p class="switch-text">¿Ya tienes cuenta?
        <a href="#" @click.prevent="$emit('switchForm')">Inicia sesión</a>
      </p>
    </div>
  </div>
</template>

<script>
export default {
  name: 'RegisterForm',
  data() {
    return {
      username: '',
      email: '',
      password: '',
      confirmPassword: '',
      userType: 'Usuario'
    };
  },
  methods: {
    register() {
      if (this.password !== this.confirmPassword) {
        alert("Las contraseñas no coinciden");
        return;
      }

      this.$emit('register');
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
  background-color: #10b981;
  color: white;
  border: none;
  border-radius: 8px;
  cursor: pointer;
  font-weight: bold;
  transition: background 0.3s;
}

button:hover {
  background-color: #059669;
}

.switch-text {
  margin-top: 1rem;
  text-align: center;
  font-size: 0.9rem;
}

.switch-text a {
  color: #10b981;
  text-decoration: none;
  font-weight: bold;
}
</style>
