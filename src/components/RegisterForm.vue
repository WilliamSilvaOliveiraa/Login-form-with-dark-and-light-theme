<template>
  <main id="container">
    <form action="" id="register_form">
      <div id="form_headerRegister">
        <h1>Register</h1>
        <i
          class="fa-solid"
          :class="{ 'fa-moon': !isDarkMode, 'fa-sun': isDarkMode }"
          id="mode_icon"
          @click="toggleDarkMode"
        ></i>
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
                :type="showPassword ? 'text' : 'password'"
                id="passwordRegister"
                name="password"
                v-model="passwordRegister"
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
        </div>
        <div class="input_box">
          <label for="confirmPasswordRegister" class="input-label">
            Confirm Password
            <div class="escudoinput">
              <i class="fa-solid fa-circle-check"></i>
              <input
                :type="showConfirmPassword ? 'text' : 'password'"
                id="confirmPasswordRegister"
                name="confirmPassword"
                v-model="confirmPasswordRegister"
                autocomplete="current-password"
              />
              <i
                :class="[
                  showConfirmPassword
                    ? 'fa-solid fa-eye eye-icon'
                    : 'fa-solid fa-eye-slash eye-icon',
                ]"
                @click="toggleConfirmPasswordVisibility"
              ></i>
            </div>
          </label>
          <div id="forgot_passwordRegister">
            <a href="#" @click.prevent="$emit('mudarFormulario')">Sign In</a>
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
      showPassword: false,
      showConfirmPassword: false,
      isDarkMode: false,
    };
  },
  mounted() {
    // Inicializa o tema e o ícone corretamente
    this.applyTheme();
  },
  methods: {
    toggleDarkMode() {
      this.isDarkMode = !this.isDarkMode; // Altera a propriedade isDarkMode
      this.applyTheme(); // Aplica o tema quando o modo escuro é alternado
    },
    applyTheme() {
      const mode = document.getElementById("mode_icon");
      const form = document.getElementById("register_form");

      if (this.isDarkMode) {
        mode.classList.remove("fa-moon");
        mode.classList.add("fa-sun");
        form.classList.add("darkRegister");
      } else {
        mode.classList.remove("fa-sun");
        mode.classList.add("fa-moon");
        form.classList.remove("darkRegister");
      }
    },
    register() {
      // Lógica para registrar o usuário com o servidor
      console.log(
        "Dados de registro:",
        this.nameRegister,
        this.emailRegister,
        this.passwordRegister
      );
    },
    togglePasswordVisibility() {
      this.showPassword = !this.showPassword;
    },
    toggleConfirmPasswordVisibility() {
      this.showConfirmPassword = !this.showConfirmPassword;
    },
  },
};
</script>

<style>
@import url("https://www.youtube.com/redirect?event=video_description&redir_token=QUFFLUhqa1d0WTBtN2R3Q2NiNndMQld2c240aXhsak94QXxBQ3Jtc0trZXYxZy16V1VCeWEzSEJrR1VCbUpDWWtKY2J0OEtlZ0hrSEk5c2ZUVlNweDJnZWVFOFl5VnBsb0Jxb00zSVhXZmF3cnpiLTRZWkZDN0phS3ZDYXYwQnRib3R0ZW9UczRJVktFV3hibURGZEVwLTk5dw&q=https%3A%2F%2Ffonts.googleapis.com%2Fcss2%3Ffamily%3DPoppins%3Awght%40100%3B200%3B300%3B400%26display%3Dswap%27%29%3B&v=qKWApkuhNu8");

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

#inputs {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  gap: 20px;
}

.input-label {
  font-size: 14px;
  color: #797984;
  width: 100%; /* Garante que a largura seja 100% do contêiner pai */
}

#register_form {
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

#form_headerRegister {
  display: flex;
  align-items: center;
  justify-content: space-between;
}

#form_headerRegister h1 {
  font-size: 40px;
  position: relative;
}

#form_headerRegister h1::before {
  position: absolute;
  content: "";
  width: 28%;
  background-color: #7c3aed;
  height: 3px;
  bottom: 4px;
  border-radius: 10px;
}

#mode_icon {
  cursor: pointer;
  font-size: 20px;
}

#forgot_passwordRegister {
  margin-top: 4px;
  justify-content: space-between; /* Adicionado para espaçamento entre os links */
  display: flex;
}

#forgot_passwordRegister a {
  text-decoration: none;
  font-size: 12px;
  color: #797984;
  margin-left: auto; /* Adicionado para alinhar à direita */
}

.escudoinput i.fa-eye {
  font-size: 18px;
  color: #000;
  margin-left: 1.125px; /* Mover o ícone eye-slash para a direita */
}

#forgot_passwordRegister a:hover {
  color: #7c3aed;
}

.escudoinput {
  display: flex;
  align-items: center;
  gap: 15px;
  padding: 3px;
  cursor: text;
  border-bottom: 1px solid #7c3aed;
  width: 340px;
}

.escudoinput i {
  font-size: 18px;
  color: #000;
}

.escudoinput .eye-icon {
  cursor: pointer; /* Adicionado cursor: pointer apenas para o ícone de olho */
}

.escudoinput input {
  border: none;
  background-color: transparent;
  width: 260px;
  font-size: 18px;
  padding: 0px 0px;
}

.escudoinput input:focus {
  outline: none;
}

#register_button {
  border: none;
  background: linear-gradient(90deg, #7c3aed, #a855f7, #bf46ef);
  color: #f8fafc;
  padding: 7px;
  font-size: 18px;
  border-radius: 3px;
  font-weight: lighter;
  cursor: pointer;
  transition: transform 0.3s ease;
}

#register_button:hover {
  transform: scale(1.05);
}

.darkRegister#register_form {
  color: #f8fafc;
  background-color: #312d37;
  animation: light-to-dark 0.3s ease-in-out;
}

.darkRegister#register_form .escudoinput input,
.darkRegister#register_form .escudoinput i {
  color: #f8fafc;
}

.darkRegister#register_form .input-label {
  color: #cfcfcf;
}

.input_box {
  width: 100%; /* Garante que a largura seja 100% do contêiner pai */
  min-width: 340px;
}

.darkRegister#register_form #forgot_passwordRegister a {
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
</style>
