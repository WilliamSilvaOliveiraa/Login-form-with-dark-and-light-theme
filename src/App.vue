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
    mudarFormulario() {
      this.mostrarRegisterForm = !this.mostrarRegisterForm;
      console.log(`Foi trocado de formulário`);
    },
  },
};
</script>

<style>
.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.5s;
}
.fade-enter, .fade-leave-to /* .fade-leave-active no <2.1.8+ */ {
  opacity: 0;
}
</style>
