<template>
<div class="min-h-screen flex justify-center items-center flex-col space-y-10 bg-gray-700">
  <h2 class="text-white">Random Password Generator App</h2>
  <div class="flex flex-col space-y-3 p-4 bg-gray-100 rounded">
    <div class="relative flex items-center">
      <input type="text" v-model="password" placeholder="Your password will be here" class="text-sm w-60 border border-green-400 rounded focus:outline-none py-2 px-4" />
      <button class="absolute right-8 mr-4" @click="copy(password)"><svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5" viewBox="0 0 20 20" fill="currentColor">
  <path d="M8 3a1 1 0 011-1h2a1 1 0 110 2H9a1 1 0 01-1-1z" />
  <path d="M6 3a2 2 0 00-2 2v11a2 2 0 002 2h8a2 2 0 002-2V5a2 2 0 00-2-2 3 3 0 01-3 3H9a3 3 0 01-3-3z" />
</svg></button>
      <button class="bg-gray-400 rounded text-white p-2 relative ml-2" @click="getPassword">
        <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5" viewBox="0 0 20 20" fill="currentColor">
  <path fill-rule="evenodd" d="M4 2a1 1 0 011 1v2.101a7.002 7.002 0 0111.601 2.566 1 1 0 11-1.885.666A5.002 5.002 0 005.999 7H9a1 1 0 010 2H4a1 1 0 01-1-1V3a1 1 0 011-1zm.008 9.057a1 1 0 011.276.61A5.002 5.002 0 0014.001 13H11a1 1 0 110-2h5a1 1 0 011 1v5a1 1 0 11-2 0v-2.101a7.002 7.002 0 01-11.601-2.566 1 1 0 01.61-1.276z" clip-rule="evenodd" />
</svg>
      </button>
    </div>
  </div>
</div>
</template>

<script>
import { ref } from 'vue'
  export default{
    setup(){
      const password = ref("");
      var passwordLength = 16;
      var chars= "1234567890abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ!@#$%^&*()_+?><:{}[]";

      function getPassword(){
        var generatedPassword ="";

        for(var i=0; i<passwordLength; i++){
          generatedPassword +=chars.charAt(Math.floor(Math.random() * chars.length));
        }
        password.value = generatedPassword
      }
      function copy(str){
        navigator.clipboard.writeText(str);
        alert('Copied');
      }

      return {password, getPassword, copy}
    }
  }
</script>

