<template>
  <div>
    <p class="h-0">|</p>
    <Navbar @change="changeTab" />
    
    <!-- Home -->
    <div v-if="currentTab === 'home'">
      <Space />

      <div class="w-screen h-screen flex items-center justify-center overflow-x-hidden">
        <Top />
      </div>

      <div class="w-screen flex items-center justify-center">
        <About />
      </div>

      <div class="w-screen flex items-center justify-center mt-16">
        <Bottom />
      </div>
    </div>

    <!-- Photography -->
    <div v-if="currentTab === 'photography'">
      <Photography />
    </div>

  </div>
</template>

<script>
import Space from './components/Space.vue'
import Top from './components/Top.vue'
import About from './components/About.vue'
import Bottom from './components/Bottom.vue'
import Navbar from './components/Navbar.vue'
import Photography from './components/Photography.vue'

export default {
  name: 'App',
  components: {
    Space,
    Top,
    About,
    Bottom,
    Navbar,
    Photography,
  },
  data() {
    return {
      currentTab: 'home', // Default tab
    };
  },
  methods: {
    changeTab(tab) {

      // Update current tab
      this.currentTab = tab;

      // Scroll to top of screen
      window.scrollTo({ top: 0 })
    }
  },
}
</script>