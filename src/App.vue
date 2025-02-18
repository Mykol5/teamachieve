<template>
  <div class="login-container">
    <!-- Left Section -->
    <div class="left-section">
      <div class="text-center">
        <img src="@/assets/logo.png" alt="Team Achieve Logo" class="logo" />
        <div class="image-container">
          <img
            src="@/assets/login-image.png"
            alt="Team Achieve"
            class="login-image"
          />
        </div>
        <h2 class="title">Team Achieve</h2>
        <p class="subtitle">Your perfect solution for funding your desires</p>
      </div>
    </div>

    <!-- Right Section -->
    <div class="right-section">
      <div class="login-box">
        <img src="@/assets/logo.png" alt="Logo" class="small-logo" />
        <h2 class="welcome-text">Welcome Back</h2>
        <p class="description">
          Enter your email address and password to access your account.
        </p>

        <!-- Login Form -->
        <form @submit.prevent="handleLogin">
          <div class="input-group">
            <label>Email Address <span class="required">*</span></label>
            <input v-model="email" type="email" class="input-field" />
          </div>

          <div class="input-group">
            <label>Password <span class="required">*</span></label>
            <div class="password-wrapper">
              <input
                v-model="password"
                :type="showPassword ? 'text' : 'password'"
                class="input-field"
              />

              <span class="toggle-password" @click="togglePassword">
                <i
                  :class="showPassword ? 'fas fa-eye-slash' : 'fas fa-eye'"
                ></i>
              </span>
            </div>
          </div>

          <div class="actions">
            <label class="remember-me">
              <input type="checkbox" /> Remember me
            </label>
            <a href="#" class="forgot-password">Forgot Password?</a>
          </div>

          <button type="submit" class="login-button">Sign In</button>
        </form>

        <p class="signup-text">
          Don't have an account?
          <a href="#" class="signup-link">Sign up</a>
        </p>
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios"; // Import axios for API calls

export default {
  data() {
    return {
      email: "",
      password: "",
      showPassword: false,
    };
  },
  methods: {
    togglePassword() {
      this.showPassword = !this.showPassword;
    },
    async handleLogin() {
      try {
        const response = await axios.post("http://localhost:3000/login", {
          email: this.email,
          password: this.password,
        });

        if (response.data.success) {
          alert("Login successful!");
          console.log("User Data:", response.data.user);
          localStorage.setItem("user", JSON.stringify(response.data.user));
          this.$router.push("/dashboard"); // Redirect to dashboard (if using Vue Router)
        } else {
          alert("Invalid email or password.");
        }
      } catch (error) {
        console.error("Login failed:", error);
        alert("Error logging in. Please try again.");
      }
    },
  },
};
</script>

<style scoped>
/* General layout */
.login-container {
  display: flex;
  min-height: 100vh;
  background-color: #ffffff;
}

/* Left Section */
.left-section {
  display: none;
  flex: 1;
  background-color: #e9d5ff;
  justify-content: center;
  align-items: center;
  padding: 40px;
}

.left-section .logo {
  width: 80px;
  height: 80px;
  margin: 0 auto;
}

.left-section .image-container {
  margin-top: 20px;
}

.left-section .login-image {
  width: 100%;
  border-radius: 10px;
  box-shadow: 0px 4px 10px rgba(0, 0, 0, 0.1);
}

.left-section .title {
  margin-top: 20px;
  font-size: 20px;
  font-weight: bold;
  color: #4b5563;
}

.left-section .subtitle {
  color: #9333ea;
  font-weight: 500;
  margin-top: 8px;
}

/* Right Section */
.right-section {
  flex: 1;
  display: flex;
  justify-content: center;
  align-items: center;
  padding: 20px;
}

.login-box {
  width: 100%;
  max-width: 400px;
  background-color: white;
  padding: 30px;
  border-radius: 10px;
  /* box-shadow: 0px 4px 10px rgba(0, 0, 0, 0.1); */
}

.small-logo {
  display: block;
  width: 64px;
  height: 64px;
  margin: 0 auto;
}

.welcome-text {
  font-size: 24px;
  font-weight: bold;
  color: #9333ea;
  text-align: center;
  margin-top: 10px;
}

.description {
  text-align: center;
  color: #6b7280;
  margin-top: 10px;
}

/* Form */
.input-group {
  margin-bottom: 15px;
}

.input-group label {
  display: block;
  color: #374151;
  font-weight: 500;
  margin-bottom: 5px;
}

.required {
  color: red;
}

.input-field {
  width: 100%;
  padding: 10px;
  border: 1px solid #d1d5db;
  border-radius: 5px;
  font-size: 16px;
}

.input-field:focus {
  outline: none;
  border-color: #9333ea;
  box-shadow: 0px 0px 4px rgba(147, 51, 234, 0.5);
}

.password-wrapper {
  position: relative;
}

.toggle-password {
  position: absolute;
  right: 10px;
  top: 50%;
  transform: translateY(-50%);
  cursor: pointer;
  color: #6b7280;
}

/* Actions */
.actions {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 15px;
}

.remember-me {
  color: #6b7280;
}

.forgot-password {
  color: #9333ea;
  text-decoration: none;
}

.forgot-password:hover {
  text-decoration: underline;
}

/* Button */
.login-button {
  width: 100%;
  background-color: #9333ea;
  color: white;
  padding: 10px;
  border-radius: 5px;
  border: none;
  font-size: 16px;
  font-weight: bold;
  cursor: pointer;
  transition: 0.3s;
}

.login-button:hover {
  background-color: #7e22ce;
}

/* Signup */
.signup-text {
  text-align: center;
  color: #6b7280;
  margin-top: 15px;
}

.signup-link {
  color: #9333ea;
  font-weight: bold;
  text-decoration: none;
}

.signup-link:hover {
  text-decoration: underline;
}

/* Responsive */
@media (min-width: 1024px) {
  .left-section {
    display: flex;
  }
}
</style>
