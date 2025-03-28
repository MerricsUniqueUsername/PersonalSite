<template>
  <div class="w-screen flex items-center justify-center z-20">
    <div class="flex flex-col items-center justify-center w-full bg-zinc-900/10 backdrop-blur-sm text-white border-t border-gray-800/50 p-6">
      <h1 class="text-3xl md:text-4xl font-bold mb-6">Some of my work</h1>

      <div class="projects flex flex-wrap items-center justify-center gap-6 md:gap-8 p-4 w-full max-w-7xl">
        <div @click="goto('https://trajectory-tuner.vercel.app/')" class="project fade w-full sm:w-[calc(50%-20px)] md:w-[calc(33%-22px)] lg:w-[calc(25%-24px)] xl:w-[340px]">
          <img src="../assets/Images/trajtuner.png" alt="Project Image" class="w-full h-48 md:h-56 lg:h-64 object-cover rounded-lg" />
          <div class="flex mt-3 justify-between items-center">
            <span class="text-lg md:text-xl font-medium">Trajectory Tuner</span>
            <GithubButton @click="goto('https://github.com/MerricsUniqueUsername/TrajectoryTuner')" />
          </div>
          <p class="text-sm md:text-base text-gray-300 mt-2">Type an expression into the input bar, and click the launch button. Try to get the trajectory of the expression to collect all the yellow coins and avoid the red coins. If fuel runs out, the player will continue in the direction it was going when fuel ran out.</p>
        </div>

        <div @click="goto('https://click-game-opal.vercel.app/')" class="project fade w-full sm:w-[calc(50%-20px)] md:w-[calc(33%-22px)] lg:w-[calc(25%-24px)] xl:w-[340px]">
          <img src="../assets/Images/clickgame.png" alt="Project Image" class="w-full h-48 md:h-56 lg:h-64 object-cover rounded-lg" />
          <div class="flex mt-3 justify-between items-center">
            <span class="text-lg md:text-xl font-medium">Click Game</span>
            <GithubButton @click="goto('https://github.com/MerricsUniqueUsername/ClickGame')"/>
          </div>
          <p class="text-sm md:text-base text-gray-300 mt-2">Click the button a given amount of times in the time limit given. Try to get the number of clicks to zero before time runs out without going negative. This game records your click speed and ranks you based on how far you get.</p>
        </div>

        <div @click="goto('https://crossword-builder-five.vercel.app/editor.html')" class="project fade w-full sm:w-[calc(50%-20px)] md:w-[calc(33%-22px)] lg:w-[calc(25%-24px)] xl:w-[340px]">
          <img src="../assets/Images/crossword.png" alt="Project Image" class="w-full h-48 md:h-56 lg:h-64 object-cover rounded-lg" />
          <div class="flex mt-3 justify-between items-center">
            <span class="text-lg md:text-xl font-medium">Crossword Builder</span>
            <GithubButton @click="goto('https://github.com/MerricsUniqueUsername/CrosswordBuilder')" />
          </div>
          <p class="text-sm md:text-base text-gray-300 mt-2">Build a crossword puzzle. Click a square to edit it, and type words into the crossword. Press the "." key to add a black square that shows symmetrically. Use arrow keys to move around and switch direction. This records the average length of your word and puts all the words you put in a list.</p>
        </div>

        <div @click="goto('https://iq-test-eight.vercel.app/')" class="project fade w-full sm:w-[calc(50%-20px)] md:w-[calc(33%-22px)] lg:w-[calc(25%-24px)] xl:w-[340px]">
          <img src="../assets/Images/test.png" alt="Project Image" class="w-full h-48 md:h-56 lg:h-64 object-cover rounded-lg" />
          <div class="flex mt-3 justify-between items-center">
            <span class="text-lg md:text-xl font-medium">Frustrating Test</span>
            <GithubButton @click="goto('https://github.com/MerricsUniqueUsername/IQTest')"/>
          </div>
          <p class="text-sm md:text-base text-gray-300 mt-2">An intentionally extremely frustrating philosophy test that tells you your IQ at the end. It attempts to make you look really bad and confused, while strawmanning your position. The whole thing is generated with AI.</p>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import { onMounted } from 'vue';
import GithubButton from './GithubButton.vue';

export default {
  components: { GithubButton },
  setup() {
    const fadeInProjects = () => {
      const projects = document.querySelectorAll('.project');

      const observerOptions = {
        threshold: 0.2
      };

      const observer = new IntersectionObserver((entries) => {
        entries.forEach((entry) => {
          if (entry.isIntersecting) {
            entry.target.classList.add('fade-in');
          }
        });
      }, observerOptions);

      projects.forEach((project) => {
        observer.observe(project);
      });
    };

    onMounted(fadeInProjects);
  },
  methods: {
    goto(url) {
      window.open(url, '_blank');
    }
  }
}
</script>

<style scoped>
.project {
  border: 1px solid rgba(58, 58, 58, 0.34);
  padding: 1rem;
  border-radius: 0.5rem;
  background-color: rgba(26, 26, 26, 0.055);
  transition: all 0.3s ease;
  overflow: auto;
  opacity: 0;
  transition: opacity 1s ease-in-out;
}

.project.fade-in {
  opacity: 1;
}

.project:hover {
  background-color: rgba(26, 26, 26, 0.384);
  transition: all 0.3s ease;
  cursor: pointer;
  border-color: rgba(110, 110, 110, 0.36);
  box-shadow: 0px 0px 10px rgba(0, 0, 0, 0.1);
}

/* Custom Scrollbar */
::-webkit-scrollbar {
  width: 10px;
  height: 10px;
}

::-webkit-scrollbar-track {
  background: rgba(26, 26, 26, 0.753);
  border-radius: 5px;
}

::-webkit-scrollbar-thumb {
  background: #363636;
  border-radius: 5px;
  border: 2px solid #333;
}

::-webkit-scrollbar-thumb:hover {
  background: #444444;
}

::-webkit-scrollbar-corner {
  background: #333;
}
</style>