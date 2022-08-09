<script setup>
import { breakpointsTailwind, useBreakpoints } from '@vueuse/core'

const breakpoints = useBreakpoints(breakpointsTailwind)

const smAndLarger = breakpoints.greater('sm')
const mobile = breakpoints.smaller('sm')

const isDisabled = ref(false)
const mobileMenuEl = ref(null)
const isMobileMenuOpen = ref(false)
const hamburgerEl = ref(null)

const handleHamburgerClick = () => {
  console.log('hamburger click')
  isDisabled.value = !isDisabled.value
  isMobileMenuOpen.value = !isMobileMenuOpen.value
  console.log(isMobileMenuOpen.value)
}

onClickOutside(mobileMenuEl, (event) => {
  console.log('click outside')
  if (event.target.value !== hamburgerEl.value)
    isMobileMenuOpen.value = false
  else isMobileMenuOpen.value = true
  isDisabled.value = false
})
</script>

<template>
  <main flex py-4 sm:py-6 sm:py-4 px-4 sm:px-6 max-w-5xl bg-white class="dark:bg-[#2D314D]" justify-between items-center container mx-auto>
    <!-- group 1 -->
    <div>
      <img v-if="isDark" class="w-[125px]" src="/images/easybank-dark-logo.svg" alt="easybank logo">
      <img v-else src="/images/logo.svg" alt="easybank logo">
    </div>

    <!-- group 2 -->
    <nav v-if="smAndLarger" flex gap-2 md:gap-4 class="text-[#9597A5] dark:text-gray-700">
      <router-link to="/">
        Home
      </router-link>
      <router-link to="/about">
        About
      </router-link>
      <router-link to="/contact">
        Contact
      </router-link>
      <router-link to="/blog">
        Blog
      </router-link>
      <router-link to="/careers">
        Careers
      </router-link>
    </nav>

    <!-- group 3 -->
    <div flex items-center>
      <!-- show button sm and up -->
      <button v-if="smAndLarger" text-sm mr-1 md:mr-4 text-white px-4 md:px-6 py-2 rounded-full class="bg-gradient-to-r from-[#33D35E] to-[#2AB6D9] dark:bg-gradient-to-r from-[#04c939] to-[#059ec5]">
        Request Invite
      </button>

      <!-- show mobile only: hamburger menu -->
      <div v-else ref="hamburgerEl" mr-4 :class="isDisabled ? 'pointer-events-none' : null" @click="handleHamburgerClick">
        <svg xmlns="http://www.w3.org/2000/svg" width="24" height="11"><g :fill="isDark ? 'white' : '#2D314D'" fill-rule="evenodd"><path d="M0 0h24v1H0zM0 5h24v1H0zM0 10h24v1H0z" /></g></svg>
      </div>

      <!-- modal menu dropdown -->
      <!-- <Teleport to="body"> -->
      <div
        v-if="isMobileMenuOpen"
        ref="mobileMenuEl"
        class="mobile-menu dark:bg-[#2D314D]"
        absolute
        z-999
        bg-white
        border-1
        border-black
        text-gray-400

        dark:text-white
        px-6
        py-4
        right-10
        rounded-lg
        top-11
      >
        <nav flex flex-col gap-2>
          <router-link to="/">
            Home
          </router-link>
          <router-link to="/about">
            About
          </router-link>
          <router-link to="/contact">
            Contact
          </router-link>
          <router-link to="/blog">
            Blog
          </router-link>
          <router-link to="/careers">
            Careers
          </router-link>
        </nav>
      </div>
      <!-- </Teleport> -->

      <!-- always show -->
      <div @click="toggleDark()">
        <div v-if="isDark" text-black dark:text-white i-carbon-sun />
        <div v-else i-carbon-moon />
      </div>
    </div>
  </main>
</template>

<style scoped>
.router-link-exact-active {
  color: black;
}
.dark .router-link-exact-active {
  color: rgb(0, 255, 247);
}

.mobile-menu {
  box-shadow: 4px 4px 0px 0px rgba(0,0,0,0.2);
}
</style>
