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

      <div id="inputsLogin">
        <div class="input_box">
          <label for="name" class="input-label">
            Name
            <div class="escudoinput">
              <i class="fa-solid fa-user"></i>
              <input
                type="text"
                id="name"
                name="name"
                autocomplete="current-name"
              />
            </div>
          </label>
        </div>
        <div class="input_box">
          <label for="email" class="input-label">
            Email
            <div class="escudoinput">
              <i class="fa-solid fa-envelope"></i>
              <input
                type="text"
                id="email"
                name="email"
                autocomplete="current-email"
              />
            </div>
          </label>
        </div>
        <div class="input_box">
          <label for="password" class="input-label">
            Password
            <div class="escudoinput">
              <i class="fa-solid fa-key"></i>
              <input
                :type="showPassword ? 'text' : 'password'"
                id="password"
                name="password"
                v-model="password"
                autocomplete="current-password"
              />
              <i
                :class="[
                  showPassword
                    ? 'fa-solid fa-eye eye-icon'
                    : 'fa-solid fa-eye-slash eye-icon',
                ]"
                @click="togglePasswordVisibility"
              ></i>
            </div>
          </label>
          <div id="forgot_password">
            <a href="#">Forgot your password?</a>
            <a href="#" @click.prevent="$emit('mudarFormulario')">Sign Up</a>
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
      showPassword: false,
    };
  },
  mounted() {
    // No momento em que o componente é montado no DOM
    const mode = document.getElementById("mode_icon");

    mode.addEventListener("click", () => {
      const form = document.getElementById("login_form");

      if (mode.classList.contains("fa-moon")) {
        mode.classList.remove("fa-moon");
        mode.classList.add("fa-sun");

        form.classList.add("dark");
        return;
      }

      mode.classList.add("fa-moon");
      mode.classList.remove("fa-sun");
      form.classList.remove("dark");
    });
  },
  methods: {
    entrar() {
      // Lógica para autenticar o usuário com o servidor
      console.log("Dados de login:", this.email, this.senha);
    },
    handleModeClick() {
      // Lógica a ser executada quando o ícone mode for clicado
      console.log("Ícone mode clicado!");
    },
    togglePasswordVisibility() {
      this.showPassword = !this.showPassword;
    },
  },
};
</script>

<style>
@import url("https://www.youtube.com/redirect?event=video_description&redir_token=QUFFLUhqa1d0WTBtN2R3Q2NiNndMQld2c240aXhsak94QXxBQ3Jtc0trZXYxZy16V1VCeWEzSEJrR1VCbUpDWWtKY2J0OEtlZ0hrSEk5c2ZUVlNweDJnZWVFOFl5VnBsb0Jxb00zSVhXZmF3cnpiLTRZWkZDN0phS3ZDYXYwQnRib3R0ZW9UczRJVktFV3hibURGZEVwLTk5dw&q=https%3A%2F%2Ffonts.googleapis.com%2Fcss2%3Ffamily%3DPoppins%3Awght%40100%3B200%3B300%3B400%26display%3Dswap%27%29%3B&v=qKWApkuhNu8");

root {
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

* {
  font-family: "Poppins", sans-serif;
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
#container {
  height: 100vh;
  width: 100%;
  background: linear-gradient(90deg, #7c3aed, #a855f7, #bf46ef);
  display: flex;
  align-items: center;
  justify-content: center;
}

#social_media {
  display: flex;
  justify-content: space-around;
}

#social_media img {
  width: 35px;
  transition: transform 0.3s ease;
}

#social_media img:hover {
  transform: scale(1.2);
}

#inputsLogin {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  gap: 40px;
}

.input-label {
  font-size: 14px;
  color: #797984;
}

#login_form {
  background-color: #f8fafc;
  display: flex;
  flex-direction: column;
  padding: 30px 40px;
  border-radius: 8px;
  gap: 30px;
  box-shadow: 5px 5px 8px rgba(0, 0, 0, 0.366);
  height: fit-content;
  animation: dark-to-light 0.3s ease-in-out;
}

#form_header {
  display: flex;
  align-items: center;
  justify-content: space-between;
}

#form_header h1 {
  font-size: 40px;
  position: relative;
}

#form_header h1::before {
  position: absolute;
  content: "";
  width: 40%;
  background-color: #7c3aed;
  height: 3px;
  bottom: 4px;
  border-radius: 10px;
}

#mode_icon {
  cursor: pointer;
  font-size: 20px;
}

.escudoinput {
  display: flex;
  align-items: center;
  gap: 15px;
  padding: 3px;
  cursor: text;
  border-bottom: 1px solid #7c3aed;
}

.escudoinput i {
  font-size: 18px;
  color: #000;
}

.escudoinput input {
  border: none;
  background-color: transparent;
  width: 260px;
  font-size: 18px;
  padding: 0px 5px;
}

.escudoinput input:focus {
  outline: none;
}

#forgot_password {
  margin-top: 4px;
  justify-content: space-between; /* Adicionado para espaçamento entre os links */
  display: flex;
}

#forgot_password a {
  text-decoration: none;
  font-size: 12px;
  color: #797984;
}

#forgot_password a:hover {
  color: #7c3aed;
}

#login_button {
  border: none;
  background: linear-gradient(90deg, #7c3aed, #a855f7, #bf46ef);
  color: #f8fafc;
  padding: 7px;
  font-size: 18px;
  border-radius: 3px;
  font-weight: lighter;
  cursor: pointer;
  transition: transform 0.3s ease;
  margin-top: 25px;
}

#login_button:hover {
  transform: scale(1.05);
}

.dark#login_form {
  color: #f8fafc;
  background-color: #312d37;
  animation: light-to-dark 0.3s ease-in-out;
}

.dark#login_form .escudoinput input,
.dark#login_form .escudoinput i {
  color: #f8fafc;
}

.dark#login_form .input-label {
  color: #cfcfcf;
}

.dark#login_form #forgot_password a {
  color: #cfcfcf;
}

@keyframes dark-to-light {
  0% {
    background-color: #312d37;
  }

  100% {
    background-color: #f8fafc;
  }
}

@keyframes light-to-dark {
  0% {
    background-color: #f8fafc;
  }

  100% {
    background-color: #312d37;
  }
}

@media screen and (max-width: 767px) {
}
</style>
