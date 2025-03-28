<template>
  <div class="min-h-screen flex justify-center items-center p-4 text-gray-100 my-24">
    <div class="w-full max-w-2xl space-y-6">
      <div>
        <h1 class="text-3xl font-bold text-transparent bg-clip-text bg-gradient-to-r from-blue-400 to-purple-600 mb-2">Psalm 19:1</h1>
        <p class="text-lg text-gray-400 italic border-l-4 border-blue-600 pl-4">
          "The heavens declare the glory of God; the skies proclaim the work of his hands."
        </p>
      </div>

      <!-- Equipment Section -->
      <div>
        <h2 class="text-2xl font-semibold text-gray-200 mb-4 mt-0!">My Basic Equipment</h2>
        
        <div class="space-y-4">
          <div class="bg-gray-800/50 rounded-lg p-4 border border-gray-700">
            <h3 class="text-xl font-medium text-blue-300 mb-2">Deep Space Photography</h3>
            <ul class="space-y-2">
              <li>
                <a 
                  href="https://www.skywatcherusa.com/products/evostar-72-apo-refractor" 
                  target="_blank" 
                  class="text-blue-400 hover:text-blue-200 transition-colors"
                >
                  SkyWatcher 72ED Telescope
                </a>
              </li>
              <li>
                <a 
                  href="https://rokinon.com/products/135mm-f2-0-full-frame-telephoto" 
                  target="_blank" 
                  class="text-blue-400 hover:text-blue-200 transition-colors"
                >
                  Rokinon 135mm F/2.0
                </a>
              </li>
              <li>
                <a 
                  href="https://www.skywatcherusa.com/products/star-adventurer-gti-mount-kit" 
                  target="_blank" 
                  class="text-blue-400 hover:text-blue-200 transition-colors"
                >
                  SkyWatcher Star Adventurer GTI Mount
                </a>
              </li>
              <li>
                <a 
                  href="https://www.amazon.com/Canon-Digital-18-55mm-discontinued-manufacturer/dp/B004J3V90Y" 
                  target="_blank" 
                  class="text-blue-400 hover:text-blue-200 transition-colors"
                >
                  Canon T3i Camera
                </a>
              </li>
            </ul>
          </div>

          <div class="bg-gray-800/50 rounded-lg p-4 border border-gray-700">
            <h3 class="text-xl font-medium text-blue-300 mb-2">Planetary Photography</h3>
            <ul class="space-y-2">
              <li>
                <a 
                  href="https://telescopes.net/orion-skyquest-xt8-plus-dobsonian-reflector-telescope.html" 
                  target="_blank" 
                  class="text-blue-400 hover:text-blue-200 transition-colors"
                >
                  Orion SkyQuest XT8 Plus Telescope (DISCONTINUED)
                </a>
              </li>
              <li>
                <a 
                  href="https://optcorp.com/products/zwo-asi120mc-s" 
                  target="_blank" 
                  class="text-blue-400 hover:text-blue-200 transition-colors"
                >
                  ZWO ASI120MC Camera
                </a>
              </li>
            </ul>
          </div>
        </div>
      </div>

      <!-- Astrophotography Section -->
      <div>

        <h2 class="text-2xl font-semibold text-gray-200 mb-4">Andromeda Galaxy</h2>
        <div class="relative">
          <img 
            :src="andromedaImage" 
            class="w-full h-auto object-cover rounded-lg shadow-2xl border border-gray-700"
          />
          <div class="absolute inset-0 bg-black/10 rounded-lg"></div>
        </div>

        <h2 class="text-2xl font-semibold text-gray-200 mb-4">Orion Nebula</h2>
        <div class="relative">
          <img 
            :src="orion" 
            class="w-full h-auto object-cover rounded-lg shadow-2xl border border-gray-700"
          />
          <div class="absolute inset-0 bg-black/10 rounded-lg"></div>
        </div>

        <h2 class="text-2xl font-semibold text-gray-200 mb-4">Lagoon and Trifid Nebula</h2>
        <div class="relative">
          <img 
            :src="lagoon" 
            class="w-full h-auto object-cover rounded-lg shadow-2xl border border-gray-700"
          />
          <div class="absolute inset-0 bg-black/10 rounded-lg"></div>
        </div>

        <h2 class="text-2xl font-semibold text-gray-200 mb-4">C/2023 A3 (Tsuchinshan–ATLAS)</h2>
        <div class="relative">
          <img 
            :src="comet" 
            class="w-full h-auto object-cover rounded-lg shadow-2xl border border-gray-700"
          />
          <div class="absolute inset-0 bg-black/10 rounded-lg"></div>
        </div>

        <h2 class="text-2xl font-semibold text-gray-200 mb-4">Leo's Triplet</h2>
        <div class="relative">
          <img 
            :src="triplet" 
            class="w-full h-auto object-cover rounded-lg shadow-2xl border border-gray-700"
          />
          <div class="absolute inset-0 bg-black/10 rounded-lg"></div>
        </div>

        <h2 class="text-2xl font-semibold text-gray-200 mb-4">Jupiter</h2>
        <div class="relative">
          <img 
            :src="jupiter" 
            class="w-full h-auto object-cover rounded-lg shadow-2xl border border-gray-700"
          />
          <div class="absolute inset-0 bg-black/10 rounded-lg"></div>
        </div>

        <h2 class="text-2xl font-semibold text-gray-200 mb-4">Jupiter Rotation Timelapse</h2>
        <div class="relative">
          <img 
            :src="timelapse" 
            class="w-full h-auto object-cover rounded-lg shadow-2xl border border-gray-700"
          />
          <div class="absolute inset-0 bg-black/10 rounded-lg"></div>
        </div>

        <h2 class="text-2xl font-semibold text-gray-200 mb-4">Saturn</h2>
        <div class="relative">
          <img 
            :src="saturn" 
            class="w-full h-auto object-cover rounded-lg shadow-2xl border border-gray-700"
          />
          <div class="absolute inset-0 bg-black/10 rounded-lg"></div>
        </div>

      </div>


    </div>
  </div>
</template>

<script>
import andromedaImage from '@/assets/Images/astro/AndromedaGalaxy.jpg'
import orion from '@/assets/Images/astro/orion.png'
import lagoon from '@/assets/Images/astro/lagoon.jpg'
import comet from '@/assets/Images/astro/Comet.png'
import triplet from '@/assets/Images/astro/triplet.jpg'
import jupiter from '@/assets/Images/astro/jupiter.png'
import timelapse from '@/assets/Images/astro/timelapse.gif'
import saturn from '@/assets/Images/astro/saturn.jpg'

export default {
  name: 'AstronomyProfile',
  data() {
    return {
      andromedaImage,
      orion,
      lagoon,
      comet,
      triplet,
      jupiter,
      timelapse,
      saturn,
    }
  }
}
</script>

<style scoped>
h2 {
  margin-top: 80px;
}
</style>