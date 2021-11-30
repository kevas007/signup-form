<template>
  <div id="app">
    <div class="bg">
    <section class="max-w-4xl p-6 mx-auto bg-white rounded-md shadow-md dark:bg-gray-800">
      <!-- <h2 class="text-lg font-semibold text-gray-700 capitalize dark:text-white">Account settings</h2> -->
      <form @submit.prevent="checkForm">
      <div v-if="errors.length">
           <div class="flex w-full max-w-sm mx-auto overflow-hidden bg-white rounded-lg shadow-md dark:bg-gray-800">
        <div class="flex items-center justify-center w-12 bg-red-500">
            <svg class="w-6 h-6 text-white fill-current" viewBox="0 0 40 40" xmlns="http://www.w3.org/2000/svg">
                <path d="M20 3.36667C10.8167 3.36667 3.3667 10.8167 3.3667 20C3.3667 29.1833 10.8167 36.6333 20 36.6333C29.1834 36.6333 36.6334 29.1833 36.6334 20C36.6334 10.8167 29.1834 3.36667 20 3.36667ZM19.1334 33.3333V22.9H13.3334L21.6667 6.66667V17.1H27.25L19.1334 33.3333Z"/>
            </svg>
        </div>
        
        <div class="px-4 py-2 -mx-3">
            <div class="mx-3">
                <span class="font-semibold text-red-500 dark:text-red-400">Error</span>
                <p class="text-sm text-gray-600 dark:text-gray-200" v-for="error in errors" :key="error">{{ error }}</p>
            </div>
        </div>
    </div>

    </div>
   
        <div class="flex flex-col mt-4 sm:grid-cols-2">
          <div>
            <label class="text-gray-700 dark:text-gray-200" for="firstName">First Name</label>
            <input
              id="firstName"
              type="text"
              v-model="firstName"
              class="block w-full px-4 py-2 mt-2 text-gray-700 bg-white border border-gray-300 rounded-md dark:bg-gray-800 dark:text-gray-300 dark:border-gray-600 focus:border-blue-500 dark:focus:border-blue-500 focus:outline-none focus:ring"
            />
          </div>
          <div>
            <label class="text-gray-700 dark:text-gray-200" for="lastName">Last Name</label>
            <input
              id="lastName"
              type="text"
              v-model="lastName"
              class="block w-full px-4 py-2 mt-2 text-gray-700 bg-white border border-gray-300 rounded-md dark:bg-gray-800 dark:text-gray-300 dark:border-gray-600 focus:border-blue-500 dark:focus:border-blue-500 focus:outline-none focus:ring"
            />
          </div>

          <div>
            <label class="text-gray-700 dark:text-gray-200" for="emailAddress">Email Address</label>
            <input
              id="emailAddress"
              type="email"
              v-model="emailAddress"
              class="block w-full px-4 py-2 mt-2 text-gray-700 bg-white border border-gray-300 rounded-md dark:bg-gray-800 dark:text-gray-300 dark:border-gray-600 focus:border-blue-500 dark:focus:border-blue-500 focus:outline-none focus:ring"
            />
          </div>

          <div>
            <label class="text-gray-700 dark:text-gray-200" for="password">Password</label>
            <input
              id="password"
              type="password"
              v-model="password"
              class="block w-full px-4 py-2 mt-2 text-gray-700 bg-white border border-gray-300 rounded-md dark:bg-gray-800 dark:text-gray-300 dark:border-gray-600 focus:border-blue-500 dark:focus:border-blue-500 focus:outline-none focus:ring"
            />
          </div>
        </div>

        <div class="flex justify-end mt-6">
          <button
            class="px-6 py-2 leading-5 text-white transition-colors duration-200 transform bg-gray-700 rounded-md hover:bg-gray-600 focus:outline-none focus:bg-gray-600"
          >Save</button>
        </div>
      </form>
    </section>

    </div>
  </div>
</template>

<script>

export default {

  name: 'App',
  data() {
    return {
      errors: [],
      firstName: null,
      lastName: null,
      emailAddress: null,
      password: null,
    };
  },
  methods: {
    checkForm: function() {
        this.errors = [];
      if (this.firstName && this.lastName && this.emailAddress && this.password) {
        return true;
      }
      if (!this.firsName ) {
      this.errors.push('First name is required');
      }
      if (!this.lastName ) {
        this.errors.push('Last name is required');
      }
      if (!this.emailAddress) {
        this.errors.push('Email required.');
      } else if (!this.validEmail(this.emailAddress)) {
        this.errors.push('Valid email required.');
      }
      if (this.password ==="") {
        this.errors.push('Password is required');
      }
        if (!this.errors.length) {

        return true;
      }
      // e.preventDefault();
    },
    validEmail: function (email) {
      var re = /^(([^<>()[\]\\.,;:\s@"]+(\.[^<>()[\]\\.,;:\s@"]+)*)|(".+"))@((\[[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\])|(([a-zA-Z\-0-9]+\.)+[a-zA-Z]{2,}))$/;
      return re.test(email);
    }

  },
}
</script>

<style>
#app {
 
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
 background-image: url("./assets/images/bg-intro-desktop.png");

  background-repeat: no-repeat;
  background-size: cover;
  background-position: center;
}
.bg{
  width: 100%;
  height: 100%;
   
}
section {
  width: 100%;


  }
</style>
