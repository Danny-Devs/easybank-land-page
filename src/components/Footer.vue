<script setup>

</script>

<template>
  <!-- flex container -->
  <main class="bg-[#2D314D]" container mx-auto max-w-5xl text-white flex sm:flex-row flex-col gap-4 sm:px-20 py-10 justify-between>
    <div flex flex-col sm:flex-row items-center>
      <!-- sm and up: column 1 -->
      <div>
        <div>
          <img class="w-[125px]" src="/images/easybank-dark-logo.svg" alt="easybank logo">
        </div>
        <div mt-10 flex gap-2 text-lg>
          <div i-carbon-logo-facebook />
          <div i-carbon-logo-youtube />
          <div i-carbon-logo-twitter />
          <div i-carbon-logo-pinterest />
          <div i-carbon-logo-instagram />
        </div>
      </div>

      <!-- sm and up: column 2 -->
      <div grid sm:grid-cols-2 grid-cols-1 text-sm content-center text-center sm:text-left sm:ml-12>
        <!-- sub-column 1 -->
        <div flex flex-col gap-4 mt-6 sm:mt-0>
          <router-link to="/about">
            About Us
          </router-link>
          <router-link to="/contact">
            Contact
          </router-link>
          <router-link to="/blog">
            Blog
          </router-link>
        </div>
        <!-- sub-column 2 -->
        <div flex flex-col gap-4 mt-6 sm:mt-0>
          <router-link to="/careers">
            Careers
          </router-link>
          <router-link to="/support">
            Support
          </router-link>
          <router-link to="/privacypolicy">
            Privacy Policy
          </router-link>
        </div>
      </div>
    </div>

    <!-- sm and up: flex right group -->
    <div sm:text-right text-center mt-4 sm:mt-0>
      <button mb-6 px-7 sm:px-4 md:px-6 py-3 sm:py-2 rounded-full class="bg-gradient-to-r from-[#33D35E] to-[#2AB6D9] dark:bg-gradient-to-r from-[#04c939] to-[#059ec5]" sm:text-sm>
        Request Invite
      </button>
      <p text-xs text-gray-300>
        © Easybank. All Rights Reserved
      </p>
    </div>
  </main>
</template>

<style scoped>

</style>
