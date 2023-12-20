<template>
  <main id="container">
    <form action="" id="register_form">
      <div id="form_header">
        <h1>Register</h1>
        <i class="fa-solid fa-moon" id="mode_icon"></i>
      </div>
      <div id="social_media">
        <a href="">
          <img src="../assets/facebook.png" alt="Facebook Logo" />
        </a>
        <a href="">
          <img src="../assets/google.png" alt="Google Logo" />
        </a>
        <a href="">
          <img src="../assets/github.png" alt="GitHub Logo" />
        </a>
      </div>

      <div id="inputs">
        <div class="input_box">
          <label for="nameRegister" class="input-label">
            Name
            <div class="escudoinput">
              <i class="fa-solid fa-user"></i>
              <input
                type="text"
                id="nameRegister"
                name="nameRegister"
                v-model="nameRegister"
              />
            </div>
          </label>
        </div>
        <div class="input_box">
          <label for="emailRegister" class="input-label">
            Email
            <div class="escudoinput">
              <i class="fa-solid fa-envelope"></i>
              <input
                type="text"
                id="emailRegister"
                name="emailRegister"
                v-model="emailRegister"
                autocomplete="current-email"
              />
            </div>
          </label>
        </div>
        <div class="input_box">
          <label for="passwordRegister" class="input-label">
            Password
            <div class="escudoinput">
              <i class="fa-solid fa-key"></i>
              <input
                type="password"
                id="passwordRegister"
                name="password"
                v-model="passwordRegister"
                autocomplete="current-password"
              />
            </div>
          </label>
          <div id="forgot_password">
            <a href="#" @click.prevent="$emit('mudarFormulario')"
              >Já possui uma conta?</a
            >
          </div>
        </div>
      </div>
      <button id="register_button" type="submit" @click.prevent="register">
        Register
      </button>
    </form>
  </main>
</template>

<script>
export default {
  data() {
    return {
      nameRegister: "",
      emailRegister: "",
      passwordRegister: "",
    };
  },
  mounted() {
    const mode = document.getElementById("mode_icon");

    mode.addEventListener("click", () => {
      // Lógica de troca de tema, semelhante à do componente de login
    });
  },
  methods: {
    register() {
      // Lógica para registrar o usuário com o servidor
      console.log(
        "Dados de registro:",
        this.nameRegister,
        this.emailRegister,
        this.passwordRegister
      );

      // Emitir evento para alternar entre formulários
      this.$emit("switchForm");
    },
  },
};
</script>

<style>
@import url("https://www.youtube.com/redirect?event=video_description&redir_token=QUFFLUhqa1d0WTBtN2R3Q2NiNndMQld2c240aXhsak94QXxBQ3Jtc0trZXYxZy16V1VCeWEzSEJrR1VCbUpDWWtKY2J0OEtlZ0hrSEk5c2ZUVlNweDJnZWVFOFl5VnBsb0Jxb00zSVhXZmF3cnpiLTRZWkZDN0phS3ZDYXYwQnRib3R0ZW9UczRJVktFV3hibURGZEVwLTk5dw&q=https%3A%2F%2Ffonts.googleapis.com%2Fcss2%3Ffamily%3DPoppins%3Awght%40100%3B200%3B300%3B400%26display%3Dswap%27%29%3B&v=qKWApkuhNu8");
</style>
