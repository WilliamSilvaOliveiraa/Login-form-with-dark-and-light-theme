<template>
  <main id="container">
    <form action="" id="login_form">
      <div id="form_header">
        <h1>Login</h1>
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
          <label for="name">
            Name
            <div class="input_field">
              <i class="fa-solid fa-user"></i>
              <input type="text" id="name" name="name" />
            </div>
          </label>
        </div>
        <div class="input_box">
          <label for="email">
            Email
            <div class="input_field">
              <i class="fa-solid fa-envelope"></i>
              <input type="text" id="email" name="email" />
            </div>
          </label>
        </div>
        <div class="input_box">
          <label for="password">
            Password
            <div class="input_field">
              <i class="fa-solid fa-key"></i>
              <input type="password" id="password" name="password" />
            </div>
          </label>
          <div id="forgot_password">
            <a href="#">Forgot your password?</a>
          </div>
        </div>
      </div>
      <button id="login_button" type="submit">Login</button>
    </form>
  </main>
</template>

<script>
export default {
  data() {
    return {
      email: "",
      senha: "",
    };
  },
  methods: {
    entrar() {
      // Lógica para autenticar o usuário com o servidor
      console.log("Dados de login:", this.email, this.senha);
    },
  },
};
</script>

<style>
:root {
  --color-light-50: #f8fafc;

  --color-dark-50: #797984;
  --color-dark-100: #312d37;
  --color-dark-900: #000;

  --color-purple-50: #7c3aed;
  --color-purple-100: #a855f7;
  --color-purple-200: #bf46ef;

  --color-gradient: linear-gradient(
    90deg,
    var(--color-purple-50),
    var(--color-purple-100),
    var(--color-purple-200)
  );
}
</style>
