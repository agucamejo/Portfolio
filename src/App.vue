<script setup>
import { ref } from 'vue'
import { Dialog, DialogPanel } from '@headlessui/vue'
import { Bars3Icon, XMarkIcon } from '@heroicons/vue/24/outline'
import AboutMe from './components/AboutMe.vue'
import Project from './components/Project.vue'
import Skills from './components/Skills.vue'
import Contact from './components/Contact.vue'

const navigation = [
  { name: 'Proyectos', href: '#Projects' },
  { name: 'Skills', href: '#Skills' },
  { name: 'Contacto', href: '#Contact' },
]

const mobileMenuOpen = ref(false);
if (
    localStorage.theme === "dark" ||
    (!("theme" in localStorage) &&
        window.matchMedia("(prefers-color-scheme: dark)").matches)
) {
    document.documentElement.classList.add("dark");
} else {
    document.documentElement.classList.remove("dark");
}

// const toggleDarkMode = ref(document.documentElement.className === "dark");
const toggleDarkMode = ref(document.documentElement.className.includes("dark"));

const changeDarkMode = () => {
    toggleDarkMode.value = document.documentElement.classList.toggle("dark");
    toggleDarkMode.value
        ? (localStorage.theme = "dark")
        : (localStorage.theme = "light");
};

</script>

<template>
  <div class="bg-white dark:bg-slate-900 dark:text-white"  >
    <div class="relative isolate pt-14 lg:px-8">
      <div class="absolute inset-x-0 -top-40 -z-10 transform-gpu overflow-hidden blur-3xl sm:-top-80" aria-hidden="true">
        <div class="relative left-[calc(50%-11rem)] aspect-[1155/678] w-[36.125rem] -translate-x-1/2 rotate-[30deg] bg-gradient-to-tr from-[#ff80b5] to-[#9089fc] opacity-30 sm:left-[calc(50%-30rem)] sm:w-[72.1875rem]" style="clip-path: polygon(74.1% 44.1%, 100% 61.6%, 97.5% 26.9%, 85.5% 0.1%, 80.7% 2%, 72.5% 32.5%, 60.2% 62.4%, 52.4% 68.1%, 47.5% 58.3%, 45.2% 34.5%, 27.5% 76.7%, 0.1% 64.9%, 17.9% 100%, 27.6% 76.8%, 76.1% 97.7%, 74.1% 44.1%)" />
      </div>
      <AboutMe class="pt-16 pb-16 mt-5 mb-5"/>
      <Project id="Projects" />
      <Skills id="Skills" />
      <Contact id="Contact" />
    </div>
  
  
  <header class="absolute inset-x-0 top-0 z-50">
      <nav class="flex items-center justify-between p-6 lg:px-8" aria-label="Global">
        <div class="flex lg:flex-1">
          <a href="#" class="-m-1.5 p-1.5">
            <span class="logo text-4xl font-semibold">AC</span>
          </a>
        </div>
        <div class="flex lg:hidden">
          <button type="button" class="-m-2.5 inline-flex items-center justify-center rounded-md p-2.5 text-gray-700" @click="mobileMenuOpen = true">
            <Bars3Icon class="h-6 w-6 dark:text-white" aria-hidden="true" />
          </button>
        </div>
        <div class="hidden lg:flex lg:gap-x-12">
          <a v-for="item in navigation" :key="item.name" :href="item.href" class="text-xl font-semibold leading-6 dark:text-white text-gray-900">{{ item.name }}</a>
        </div>
        <div class="hidden lg:flex lg:flex-1 lg:justify-end" >
          <div class="toggle-switch" >
                  <label class="switch-label">
                    <input type="checkbox" class="checkbox" @click="changeDarkMode">
                    <span class="slider"></span>
                  </label>
                </div>  
          </div>
      </nav>

      
      <Dialog as="div" class="lg:hidden" @close="mobileMenuOpen = false" :open="mobileMenuOpen">
        <div class="fixed inset-0 z-50" />
        <DialogPanel class="fixed inset-y-0 right-0 z-50 w-full overflow-y-auto bg-white dark:bg-slate-900  px-6 py-6 sm:max-w-sm sm:ring-1 sm:ring-gray-900/10">
          <div class="flex items-center justify-between">
            <a href="#" class="-m-1.5 p-1.5">
            </a>
            <button type="button" class="-m-2.5 rounded-md p-2.5 text-gray-700 dark:text-white" @click="mobileMenuOpen = false">
              <XMarkIcon class="h-6 w-6" aria-hidden="true" />
            </button>
          </div>
          <div class="mt-6 flow-root">
            <div class="-my-6 divide-y divide-gray-500/10">
              <div class="space-y-2 py-6">
                <a v-for="item in navigation" :key="item.name" :href="item.href" class="-mx-3 block rounded-lg px-3 py-2 text-base font-semibold leading-7 text-gray-900 dark:text-white dark:hover:bg-slate-600 hover:bg-gray-50">{{ item.name }}</a>
              </div>
              <div class="py-6">
                <div class="toggle-switch"  >
                  <label class="switch-label">
                    <input type="checkbox" class="checkbox" @click="changeDarkMode">
                    <span class="slider"></span>
                  </label>
                </div>  
              </div>
            </div>
          </div>
        </DialogPanel>
      </Dialog>
    </header>
  </div>
</template>

<style>
  @import url('https://fonts.googleapis.com/css2?family=Open+Sans:wght@300;400;600&family=Playfair+Display:wght@900&display=swap');

  .logo{
    font-family: Playfair;
    font-weight: 900;
  }

</style>