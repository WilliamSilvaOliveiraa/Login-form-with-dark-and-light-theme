<template>
  <div>
    <div v-if="mostrarRegisterForm">
      <RegisterForm @mudarFormulario="mudarFormulario" />
    </div>
    <div v-else>
      <LoginForm @mudarFormulario="mudarFormulario" />
    </div>
  </div>
</template>

<script>
import LoginForm from "./components/LoginForm.vue";

import RegisterForm from "./components/RegisterForm.vue";

export default {
  data() {
    return {
      mostrarRegisterForm: true,
    };
  },
  name: "App",
  components: {
    LoginForm,
    RegisterForm,
  },
  methods: {
    switchForm() {
      this.showLoginForm = !this.showLoginForm;
      console.log(
        `Evento switchForm emitido. Exibir formulário de login: ${this.showLoginForm}`
      );
    },
    mudarFormulario() {
      this.mostrarRegisterForm = !this.mostrarRegisterForm;
      console.log(`Foi trocado de formulario`);
    },
  },
};
</script>

<style>
.slide-fade-enter-active,
.slide-fade-leave-active {
  transition: opacity 0.5s, transform 0.5s;
}
.slide-fade-enter, .slide-fade-leave-to /* .slide-fade-leave-active in <2.1.8 */ {
  opacity: 0;
  transform: translateX(30px);
}
</style>
