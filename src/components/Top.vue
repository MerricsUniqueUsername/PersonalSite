<template>
  <div ref="container" 
       class="border-t border-b border-gray-500/20 z-10 overflow-hidden transition-all duration-500 backdrop-blur-sm relative flex justify-center items-center bg-gradient-to-br from-gray-900/50 via-gray-700/45 to-black"
       :class="{ 'h-[80vh] md:h-2/3': isOpen, 'h-0': !isOpen, 'w-screen': isWide, 'w-0': !isWide }">
    <div class="absolute inset-0 bg-black opacity-60"></div>

    <div class="opacity-0 transition-opacity duration-800 w-11/12 max-w-6xl text-center z-50 border-l border-r border-gray-700/25 h-full flex flex-col md:flex-row"
         :class="{ 'opacity-100': isOpen }">

      <div class="w-full md:w-4/5 h-1/2 md:h-full text-white flex flex-col justify-center p-4 md:p-10 space-y-4 md:space-y-6 order-1 md:order-none">
        <div>
          <h1 class="text-3xl md:text-5xl font-bold tracking-tight bg-clip-text text-white">Hello, I am Merric</h1>
          <p class="text-base md:text-xl mt-2 text-gray-300">I am a 20 year old computer science major from <span class="text-yellow-200 font-semibold">Michigan Technological University</span></p>
        </div>

        <!-- Social Links -->
        <div class="flex items-center justify-center space-x-4 md:space-x-6">
          <!-- GitHub -->
          <div class="social-container group relative">
            <a @click="showContact('github', 'MerricsUniqueUsername')" class="social-icon hover:scale-110 transition-transform block cursor-pointer">
              <svg xmlns="http://www.w3.org/2000/svg" width="20" height="20" fill="currentColor" class="bi bi-github" viewBox="0 0 16 16">
                <path d="M8 0C3.58 0 0 3.58 0 8c0 3.54 2.29 6.53 5.47 7.59.4.07.55-.17.55-.38 0-.19-.01-.82-.01-1.49-2.01.37-2.53-.49-2.69-.94-.09-.23-.48-.94-.82-1.13-.28-.15-.68-.52-.01-.53.63-.01 1.08.58 1.23.82.72 1.21 1.87.87 2.33.66.07-.52.28-.87.51-1.07-1.78-.2-3.64-.89-3.64-3.95 0-.87.31-1.59.82-2.15-.08-.2-.36-1.02.08-2.12 0 0 .67-.21 2.2.82.64-.18 1.32-.27 2-.27s1.36.09 2 .27c1.53-1.04 2.2-.82 2.2-.82.44 1.1.16 1.92.08 2.12.51.56.82 1.27.82 2.15 0 3.07-1.87 3.75-3.65 3.95.29.25.54.73.54 1.48 0 1.07-.01 1.93-.01 2.2 0 .21.15.46.55.38A8.01 8.01 0 0 0 16 8c0-4.42-3.58-8-8-8"/>
              </svg>
            </a>
            <span class="absolute left-1/2 transform -translate-x-1/2 mt-6 text-xs text-gray-300 opacity-0 group-hover:opacity-100 transition-opacity duration-300">GitHub</span>
          </div>

          <!-- Email -->
          <div class="social-container group relative">
            <a @click="showContact('email', 'merricjustian@gmail.com')" class="social-icon hover:scale-110 transition-transform block cursor-pointer">
              <svg xmlns="http://www.w3.org/2000/svg" width="20" height="20" fill="currentColor" class="bi bi-envelope" viewBox="0 0 16 16">
                <path d="M0 4a2 2 0 0 1 2-2h12a2 2 0 0 1 2 2v8a2 2 0 0 1-2 2H2a2 2 0 0 1-2-2zm2-1a1 1 0 0 0-1 1v.217l7 4.2 7-4.2V4a1 1 0 0 0-1-1zm13 2.383-4.708 2.825L15 11.105zm-.034 6.876-5.64-3.471L8 9.583l-1.326-.795-5.64 3.47A1 1 0 0 0 2 13h12a1 1 0 0 0 .966-.741M1 11.105l4.708-2.897L1 5.383z"/>
              </svg>
            </a>
            <span class="absolute left-1/2 transform -translate-x-1/2 mt-6 text-xs text-gray-300 opacity-0 group-hover:opacity-100 transition-opacity duration-300">Email</span>
          </div>

          <!-- Phone -->
          <div class="social-container group relative">
            <a @click="showContact('phone', '(734) 642-6713')" class="social-icon hover:scale-110 transition-transform block cursor-pointer">
              <svg xmlns="http://www.w3.org/2000/svg" width="20" height="20" fill="currentColor" class="bi bi-telephone" viewBox="0 0 16 16">
                <path d="M3.654 1.328a.678.678 0 0 0-1.015-.063L1.605 2.3c-.483.484-.661 1.169-.45 1.77a17.6 17.6 0 0 0 4.168 6.608 17.6 17.6 0 0 0 6.608 4.168c.601.211 1.286.033 1.77-.45l1.034-1.034a.678.678 0 0 0-.063-1.015l-2.307-1.794a.68.68 0 0 0-.58-.122l-2.19.547a1.75 1.75 0 0 1-1.657-.459L5.482 8.062a1.75 1.75 0 0 1-.46-1.657l.548-2.19a.68.68 0 0 0-.122-.58zM1.884.511a1.745 1.745 0 0 1 2.612.163L6.29 2.98c.329.423.445.974.315 1.494l-.547 2.19a.68.68 0 0 0 .178.643l2.457 2.457a.68.68 0 0 0 .644.178l2.189-.547a1.75 1.75 0 0 1 1.494.315l2.306 1.794c.829.645.905 1.87.163 2.611l-1.034 1.034c-.74.74-1.846 1.065-2.877.702a18.6 18.6 0 0 1-7.01-4.42 18.6 18.6 0 0 1-4.42-7.009c-.362-1.03-.037-2.137.703-2.877z"/>
              </svg>
            </a>
            <span class="absolute left-1/2 transform -translate-x-1/2 mt-6 text-xs text-gray-300 opacity-0 group-hover:opacity-100 transition-opacity duration-300">Phone</span>
          </div>

          <!-- Discord -->
          <div class="social-container group relative">
            <a @click="showContact('discord', 'merric4421')" class="social-icon hover:scale-110 transition-transform block cursor-pointer">
              <svg xmlns="http://www.w3.org/2000/svg" width="20" height="20" fill="currentColor" class="bi bi-discord" viewBox="0 0 16 16">
                <path d="M13.545 2.907a13.2 13.2 0 0 0-3.257-1.011.05.05 0 0 0-.052.025c-.141.25-.297.577-.406.833a12.2 12.2 0 0 0-3.658 0 8 8 0 0 0-.412-.833.05.05 0 0 0-.052-.025c-1.125.194-2.22.534-3.257 1.011a.04.04 0 0 0-.021.018C.356 6.024-.213 9.047.066 12.032q.003.022.021.037a13.3 13.3 0 0 0 3.995 2.02.05.05 0 0 0 .056-.019q.463-.63.818-1.329a.05.05 0 0 0-.01-.059l-.018-.011a9 9 0 0 1-1.248-.595.05.05 0 0 1-.02-.066l.015-.019q.127-.095.248-.195a.05.05 0 0 1 .051-.007c2.619 1.196 5.454 1.196 8.041 0a.05.05 0 0 1 .053.007q.121.1.248.195a.05.05 0 0 1-.004.085 8 8 0 0 1-1.249.594.05.05 0 0 0-.03.03.05.05 0 0 0 .003.041c.24.465.515.909.817 1.329a.05.05 0 0 0 .056.019 13.2 13.2 0 0 0 4.001-2.02.05.05 0 0 0 .021-.037c.334-3.451-.559-6.449-2.366-9.106a.03.03 0 0 0-.02-.019m-8.198 7.307c-.789 0-1.438-.724-1.438-1.612s.637-1.613 1.438-1.613c.807 0 1.45.73 1.438 1.613 0 .888-.637 1.612-1.438 1.612m5.316 0c-.788 0-1.438-.724-1.438-1.612s.637-1.613 1.438-1.613c.807 0 1.451.73 1.438 1.613 0 .888-.631 1.612-1.438 1.612"/>
              </svg>
            </a>
            <span class="absolute left-1/2 transform -translate-x-1/2 mt-6 text-xs text-gray-300 opacity-0 group-hover:opacity-100 transition-opacity duration-300">Discord</span>
          </div>

          <!-- Instagram -->
          <div class="social-container group relative">
            <a @click="showContact('instagram', '@_merric_')" class="social-icon hover:scale-110 transition-transform block cursor-pointer">
              <svg xmlns="http://www.w3.org/2000/svg" width="20" height="20" fill="currentColor" class="bi bi-instagram" viewBox="0 0 16 16">
                <path d="M8 0C5.829 0 5.556.01 4.703.048 3.85.088 3.269.222 2.76.42a3.9 3.9 0 0 0-1.417.923A3.9 3.9 0 0 0 .42 2.76C.222 3.268.087 3.85.048 4.7.01 5.555 0 5.827 0 8.001c0 2.172.01 2.444.048 3.297.04.852.174 1.433.372 1.942.205.526.478.972.923 1.417.444.445.89.719 1.416.923.51.198 1.09.333 1.942.372C5.555 15.99 5.827 16 8 16s2.444-.01 3.298-.048c.851-.04 1.434-.174 1.943-.372a3.9 3.9 0 0 0 1.416-.923c.445-.445.718-.891.923-1.417.197-.509.332-1.09.372-1.942C15.99 10.445 16 10.173 16 8s-.01-2.445-.048-3.299c-.04-.851-.175-1.433-.372-1.941a3.9 3.9 0 0 0-.923-1.417A3.9 3.9 0 0 0 13.24.42c-.51-.198-1.092-.333-1.943-.372C10.443.01 10.172 0 7.998 0zm-.717 1.442h.718c2.136 0 2.389.007 3.232.046.78.035 1.204.166 1.486.275.373.145.64.319.92.599s.453.546.598.92c.11.281.24.705.275 1.485.039.843.047 1.096.047 3.231s-.008 2.389-.047 3.232c-.035.78-.166 1.203-.275 1.485a2.5 2.5 0 0 1-.599.919c-.28.28-.546.453-.92.598-.28.11-.704.24-1.485.276-.843.038-1.096.047-3.232.047s-2.39-.009-3.233-.047c-.78-.036-1.203-.166-1.485-.276a2.5 2.5 0 0 1-.92-.598 2.5 2.5 0 0 1-.6-.92c-.109-.281-.24-.705-.275-1.485-.038-.843-.046-1.096-.046-3.233s.008-2.388.046-3.231c.036-.78.166-1.204.276-1.486.145-.373.319-.64.599-.92s.546-.453.92-.598c.282-.11.705-.24 1.485-.276.738-.034 1.024-.044 2.515-.045zm4.988 1.328a.96.96 0 1 0 0 1.92.96.96 0 0 0 0-1.92m-4.27 1.122a4.109 4.109 0 1 0 0 8.217 4.109 4.109 0 0 0 0-8.217m0 1.441a2.667 2.667 0 1 1 0 5.334 2.667 2.667 0 0 1 0-5.334"/>
              </svg>
            </a>
            <span class="absolute left-1/2 transform -translate-x-1/2 mt-6 text-xs text-gray-300 opacity-0 group-hover:opacity-100 transition-opacity duration-300">Instagram</span>
          </div>
        </div>

        <!-- Contact Info Display -->
        <div v-if="activeContact" class="mt-4 p-3 bg-gray-800/80 rounded-lg transition-all duration-300">
          <p class="text-sm text-gray-300">{{ activeContactLabel }}:</p>
          <p class="text-white font-medium break-all">{{ activeContactValue }}</p>
          <button @click="copyToClipboard" class="mt-2 px-3 py-1 bg-gray-700 hover:bg-gray-600 rounded text-xs text-white transition-colors">
            Copy
          </button>
        </div>
      </div>

      <div class="w-full md:w-1/2 h-1/2 md:h-full flex items-center justify-center p-4 md:pr-10 order-0 md:order-none">
        <div class="w-48 h-48 md:w-84 md:h-84 rounded-full overflow-hidden border-2 border-gray-700 shadow-2xl">
          <img src="../assets/Images/me.jpg" class="w-full h-full object-cover" alt="Merric's Profile">
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      isWide: false,
      isOpen: false,
      activeContact: null,
      activeContactLabel: '',
      activeContactValue: '',
      isMobile: false
    };
  },
  mounted() {
    this.isMobile = window.innerWidth < 768;
    
    setTimeout(() => {
      this.isWide = true;
    }, 100);
    setTimeout(() => {
      this.isOpen = true;
    }, 600);
  },
  methods: {
    showContact(type, value) {      
      this.activeContact = type;
      this.activeContactLabel = type.charAt(0).toUpperCase() + type.slice(1);
      this.activeContactValue = value;
    },
    copyToClipboard() {
      if (!this.activeContactValue) return;
      
      navigator.clipboard.writeText(this.activeContactValue)
        .then(() => {
          const originalText = this.activeContactLabel;
          this.activeContactLabel = 'Copied';
          setTimeout(() => {
            this.activeContactLabel = originalText;
          }, 1000);
        })
        .catch(err => {
          console.error('Failed to copy: ', err);
        });
    }
  }
};
</script>

<style scoped>
.social-container {
  display: inline-flex;
  flex-direction: column;
  align-items: center;
  min-height: 40px; /* Add minimum height to accommodate the label */
}
</style>