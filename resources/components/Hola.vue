<template>
    <div class="container">
      <div class="card">
        <h1 id="heading">Iniciar Sesión</h1>
        <form @submit.prevent="handleSubmit" class="form">
          <div class="field">
            <svg class="input-icon" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24">
              <path d="M12 12c2.21 0 4-1.79 4-4s-1.79-4-4-4-4 1.79-4 4 1.79 4 4 4zm0 2c-3.31 0-6 2.69-6 6v1h12v-1c0-3.31-2.69-6-6-6zm0-10c1.1 0 2 .9 2 2s-.9 2-2 2-2-.9-2-2 .9-2 2-2z"/>
            </svg>
            <input
              type="email"
              id="email"
              v-model="form.email"
              class="input-field"
              placeholder="Introduce tu correo electrónico"
              required
            />
          </div>
          <div class="field">
            <svg class="input-icon" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24">
              <path d="M12 12c2.21 0 4-1.79 4-4s-1.79-4-4-4-4 1.79-4 4 1.79 4 4 4zm0 2c-3.31 0-6 2.69-6 6v1h12v-1c0-3.31-2.69-6-6-6zm0-10c1.1 0 2 .9 2 2s-.9 2-2 2-2-.9-2-2 .9-2 2-2z"/>
            </svg>
            <input
              type="password"
              id="password"
              v-model="form.password"
              class="input-field"
              placeholder="Introduce tu contraseña"
              required
            />
          </div>
          <div class="btn-container">
            <button type="submit" class="button button-primary">Iniciar Sesión</button>
            <a href="/signup" class="button button-secondary">Regístrate</a>
          </div>
        </form>
      </div>
    </div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        form: {
          email: '',
          password: ''
        },
        errors: {}
      };
    },
    methods: {
      handleSubmit() {
        this.errors = this.validateForm();
        if (Object.keys(this.errors).length === 0) {
          // Aquí puedes manejar la lógica de inicio de sesión
          console.log('Formulario enviado:', this.form);
        }
      },
      validateForm() {
        const errors = {};
        if (!this.form.email) {
          errors.email = 'El correo electrónico es requerido.';
        } else if (!/\S+@\S+\.\S+/.test(this.form.email)) {
          errors.email = 'El correo electrónico no es válido.';
        }
        if (!this.form.password) {
          errors.password = 'La contraseña es requerida.';
        }
        return errors;
      }
    }
  };
  </script>
  
 
  