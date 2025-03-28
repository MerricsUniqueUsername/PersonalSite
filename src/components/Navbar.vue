<template>
  <div class="fixed w-full h-24 flex justify-center items-center z-100">

    <div class="bg-zinc-900/55 h-12 backdrop-blur-lg w-4/5 z-100 rounded-md border border-zinc-700/50 shadow-md flex items-center justify-center">

      <a @click="changeTab('home')" class="text-gray-300 text-lg font-semibold hover:text-white transition duration-300 mx-4">Home</a>
      <a @click="changeTab('photography')" class="text-gray-300 text-lg font-semibold hover:text-white transition duration-300 mx-4">Photography</a>
      <a href="https://github.com/MerricsUniqueUsername/PersonalSite" target="_blank" class="text-gray-300 text-lg font-semibold hover:text-white transition duration-300 mx-4">Source</a>

    </div>

  </div>
</template>

<script>
export default {
  emits: ['change'],
  name: 'Navbar',
  methods: {
    changeTab(tab) {
      this.$emit('change', tab);
    }
  }
}
</script>

<style scoped>
a {
  cursor: pointer;
}
</style>