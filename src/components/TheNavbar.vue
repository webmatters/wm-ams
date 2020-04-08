`<template>
  <header class="bg-white">
    <div class="container mx-auto p-4 md:flex md:justify-between md:items-center">
      <!-- Brand Logo -->
      <div>
        <a
          v-if="$route.path === '/'"
          href="/#top"
          v-scroll-to="{
            el: '#top',
            offset: -153,
          }"
        >
          <g-image src="~/assets/img/brand.svg" alt="Web Matters logo" class="w-full" />
        </a>
        <g-link v-else to="/">
          <g-image src="~/assets/img/brand.svg" alt="Web Matters logo" class="w-full" />
        </g-link>
      </div>
      <!-- Email address -->
      <div class="mt-6 md:mt-0 flex items-center">
        <email-icon class="text-primary" />
        <div class="ml-4">
          <div class="font-semibold">Email</div>
          <div class="text-gray-700 text-sm">info@webmatters.io</div>
        </div>
      </div>
      <!-- Call to Action button -->
      <div class="mt-4 md:mt-0">
        <a
          v-if="$route.path === '/'"
          href="/#contact"
          v-scroll-to="'#contact'"
          class="block btn-grad text-center rounded-full text-white py-2 px-4 md:ml-6 mt-3 md:mt-0 uppercase"
        >Free Strategy Session</a>
        <g-link
          v-else
          to="/#contact"
          class="block btn-grad text-center rounded-full text-white py-2 px-4 md:ml-6 mt-3 md:mt-0 uppercase"
        >Free Strategy Session</g-link>
      </div>
    </div>
    <!-- End pre-Navbar section -->

    <div class="flex items-center bg-primary justify-between px-4 py-4 md:p-0">
      <div class="md:hidden flex items-center justify-between">
        <button
          @click="isOpen = !isOpen"
          type="button"
          class="focus:outline-none text-gray-400 hover:text-gray-100"
        >
          <menu-icon v-if="!isOpen" class="fill-current" :size="32" />
          <close-icon v-else class="fill-current" :size="32" />
        </button>
        <div class="ml-2 uppercase text-xl text-gray-400">Menu</div>
      </div>
      <search-input class="md:hidden text-gray-400" />
    </div>
    <!-- End Mobile Menu Toggler -->

    <div class="md:bg-secondary">
      <div class="container mx-auto px-4 md:flex md:items-center md:justify-between">
        <ul
          :class="isOpen ? 'block' : 'hidden'"
          class="md:flex md:items-center p-4 md:px-0 text-secondary md:text-gray-300 text-lg"
        >
          <li class="mt-2">
            <a
              v-if="$route.path === '/'"
              href="/#services"
              v-scroll-to="{
                el: '#services',
                offset: -153,
              }"
              class="nav-link md:hover:text-white md:mt-0"
            >Services</a>
            <g-link
              v-else
              to="/#services"
              class="nav-link hover:text-primary md:hover:text-white md:mt-0"
            >Services</g-link>
          </li>
          <li class="mt-2">
            <a
              v-if="$route.path === '/'"
              href="/#about"
              v-scroll-to="{
                el: '#about',
                offset: -153,
              }"
              class="nav-link hover:text-primary md:hover:text-white md:ml-6 md:mt-0"
            >About</a>
            <g-link
              v-else
              to="/#about"
              class="nav-link hover:text-primary md:hover:text-white md:ml-6 md:mt-0"
            >About</g-link>
          </li>
          <li class="mt-2">
            <g-link
              to="/blog"
              class="nav-link hover:text-primary md:hover:text-white md:ml-6 md:mt-0"
            >Blog</g-link>
          </li>
          <li class="mt-2">
            <a
              v-if="$route.path === '/'"
              href="/#contact"
              v-scroll-to="'#contact'"
              class="nav-link hover:text-primary md:hover:text-white md:ml-6 md:mt-0"
            >Contact</a>
            <g-link
              v-else
              to="/#contact"
              class="nav-link hover:text-primary md:hover:text-white md:ml-6 md:mt-0"
            >Contact</g-link>
          </li>
        </ul>
        <search-input
          class="hidden md:inline-block md:text-gray-300 md:bg-secondary md:hover:text-white"
        />
      </div>
      <!-- End Navbar -->
    </div>
  </header>
</template>

<script>
import MenuIcon from 'vue-material-design-icons/Menu.vue'
import CloseIcon from 'vue-material-design-icons/Close.vue'
import EmailIcon from 'vue-material-design-icons/Email.vue'
import SearchInput from '@/components/SearchInput.vue'

export default {
  components: {
    MenuIcon,
    CloseIcon,
    EmailIcon,
    SearchInput,
  },
  data() {
    return {
      isOpen: false,
    }
  },
}
</script>

<style scoped>
.btn-grad {
  background-image: linear-gradient(to right, #ff512f 0%, #f09819 100%);
}
</style>
