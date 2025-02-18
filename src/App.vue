<template>
  <div class="flex min-h-screen bg-gray-100">
    <!-- Left Section -->
    <div
      class="hidden lg:flex w-1/2 bg-purple-100 justify-center items-center p-10"
    >
      <div class="text-center">
        <img
          src="@/assets/logo.png"
          alt="Team Achieve Logo"
          class="mx-auto w-20 h-20"
        />
        <div class="mt-6">
          <img
            src="@/assets/login-image.png"
            alt="Team Achieve"
            class="rounded-lg shadow-lg w-full"
          />
        </div>
        <h2 class="mt-6 text-lg font-semibold text-gray-800">Team Achieve</h2>
        <p class="text-purple-700 font-medium mt-2">
          Your perfect solution for funding your desires
        </p>
      </div>
    </div>

    <!-- Right Section -->
    <div class="w-full lg:w-1/2 flex justify-center items-center p-8">
      <div class="max-w-md w-full bg-white p-8 shadow-md rounded-lg">
        <img src="@/assets/logo.png" alt="Logo" class="mx-auto w-16 h-16" />
        <h2 class="text-2xl font-bold text-purple-700 text-center mt-4">
          Welcome Back
        </h2>
        <p class="text-center text-gray-500 mt-2">
          Enter your email address and password to access your account.
        </p>

        <!-- Login Form -->
        <form @submit.prevent="handleLogin" class="mt-6">
          <div class="mb-4">
            <label class="block text-gray-700 font-medium"
              >Email Address <span class="text-red-500">*</span></label
            >
            <input
              v-model="email"
              type="email"
              class="w-full px-4 py-2 border rounded-md focus:outline-none focus:ring-2 focus:ring-purple-600"
            />
          </div>

          <div class="mb-4">
            <label class="block text-gray-700 font-medium"
              >Password <span class="text-red-500">*</span></label
            >
            <div class="relative">
              <input
                v-model="password"
                :type="showPassword ? 'text' : 'password'"
                class="w-full px-4 py-2 border rounded-md focus:outline-none focus:ring-2 focus:ring-purple-600"
              />
              <span
                class="absolute right-3 top-2 cursor-pointer"
                @click="togglePassword"
              >
                <i
                  :class="showPassword ? 'fas fa-eye-slash' : 'fas fa-eye'"
                ></i>
              </span>
            </div>
          </div>

          <div class="flex justify-between items-center mb-4">
            <label class="flex items-center text-gray-600">
              <input type="checkbox" class="mr-2" /> Remember me
            </label>
            <a href="#" class="text-purple-600 hover:underline"
              >Forgot Password?</a
            >
          </div>

          <button
            type="submit"
            class="w-full bg-purple-700 text-white py-2 rounded-md hover:bg-purple-800 transition"
          >
            Sign In
          </button>
        </form>

        <p class="text-center text-gray-600 mt-4">
          Don't have an account?
          <a href="#" class="text-purple-600 font-semibold hover:underline"
            >Sign up</a
          >
        </p>
      </div>
    </div>
  </div>
</template>

<script>
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
    handleLogin() {
      console.log("Logging in with:", this.email, this.password);
    },
  },
};
</script>

<style scoped>
@media (max-width: 1024px) {
  .login-container {
    flex-direction: column;
  }
}
</style>
