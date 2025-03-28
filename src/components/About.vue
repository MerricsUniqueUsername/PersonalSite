<template>
  <div class="bg-gradient-to-br from-slate-900 via-black to-indigo-950 min-h-screen py-12 px-4">
    <div class="w-full max-w-6xl mx-auto bg-gray-800/10 backdrop-blur-xs rounded-2xl border border-gray-700/50 overflow-hidden shadow-2xl">
      <div class="relative">
        
        <div class="relative z-10 w-full max-w-5xl mx-auto p-6">
          <h1 class="text-white font-bold text-5xl text-center mb-6">About me</h1>
          
          <p class="text-gray-400 text-lg text-center max-w-3xl mx-auto mb-12 leading-relaxed">
            I got into programming when I was 14 years old to make video games. As of now, I mostly use my programming
            skills to process images, make web applications, or make anything that I just find really interesting.
            Outside of programming, I enjoy hiking, astrophotography, broomball, and thinking way too much about
            philosophical questions that are not realistically answerable.
          </p>

          <div class="space-y-8" ref="experience">
            <div class="bg-gray-800/10 backdrop-blur-sm rounded-xl p-6 border border-gray-800/50">
              <h2 class="text-gray-400 text-xl mb-6 text-center">Languages</h2>
              <div class="flex flex-wrap justify-center gap-6">
                <div class="tool-item group">
                  <img src="../assets/Images/Icons/c.png" class="w-16 h-16 object-contain group-hover:scale-110 transition-transform">
                  <p class="mt-2 text-gray-300">C</p>
                </div>
                <div class="tool-item group">
                  <img src="../assets/Images/Icons/python.png" class="w-16 h-16 object-contain group-hover:scale-110 transition-transform">
                  <p class="mt-2 text-gray-300">Python</p>
                </div>
                <div class="tool-item group">
                  <img src="../assets/Images/Icons/java.png" class="w-16 h-16 object-contain group-hover:scale-110 transition-transform">
                  <p class="mt-2 text-gray-300">Java</p>
                </div>
                <div class="tool-item group">
                  <img src="../assets/Images/Icons/javascript.png" class="w-16 h-16 object-contain group-hover:scale-110 transition-transform">
                  <p class="mt-2 text-gray-300">JavaScript</p>
                </div>
                <div class="tool-item group">
                  <img src="../assets/Images/Icons/html.png" class="w-16 h-16 object-contain group-hover:scale-110 transition-transform">
                  <p class="mt-2 text-gray-300">HTML</p>
                </div>
                <div class="tool-item group">
                  <img src="../assets/Images/Icons/css.png" class="w-16 h-16 object-contain group-hover:scale-110 transition-transform">
                  <p class="mt-2 text-gray-300">CSS</p>
                </div>
              </div>
            </div>

            <div class="bg-gray-800/10 backdrop-blur-sm rounded-xl p-6 border border-gray-800/50">
              <h2 class="text-gray-400 text-xl mb-6 text-center">Web Development</h2>
              <div class="flex flex-wrap justify-center gap-6">
                <div class="tool-item group">
                  <img src="../assets/Images/Icons/vue.png" class="w-16 h-16 object-contain group-hover:scale-110 transition-transform">
                  <p class="mt-2 text-gray-300">Vue</p>
                </div>
                <div class="tool-item group">
                  <img src="../assets/Images/Icons/vite.png" class="w-16 h-16 object-contain group-hover:scale-110 transition-transform">
                  <p class="mt-2 text-gray-300">Vite</p>
                </div>
                <div class="tool-item group">
                  <img src="../assets/Images/Icons/django.png" class="w-16 h-16 object-contain group-hover:scale-110 transition-transform">
                  <p class="mt-2 text-gray-300">Django</p>
                </div>
                <div class="tool-item group">
                  <img src="../assets/Images/Icons/tailwind.png" class="w-16 h-16 object-contain group-hover:scale-110 transition-transform">
                  <p class="mt-2 text-gray-300">Tailwind</p>
                </div>
                <div class="tool-item group">
                  <img src="../assets/Images/Icons/mysql.png" class="w-16 h-16 object-contain group-hover:scale-110 transition-transform">
                  <p class="mt-2 text-gray-300">MySQL</p>
                </div>
                <div class="tool-item group">
                  <img src="../assets/Images/Icons/vercel.png" class="w-16 h-16 object-contain group-hover:scale-110 transition-transform">
                  <p class="mt-2 text-gray-300">Vercel</p>
                </div>
                <div class="tool-item group">
                  <img src="../assets/Images/Icons/sqlite.png" class="w-16 h-16 object-contain group-hover:scale-110 transition-transform">
                  <p class="mt-2 text-gray-300">SQLite</p>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  mounted() {
    this.$nextTick(() => {
      const experience = this.$refs.experience;
      const tools = experience.querySelectorAll('.tool-item');
      const fac = new FastAverageColor();

      tools.forEach(tool => {
        const img = tool.querySelector('img');
        const label = tool.querySelector('p');

        // Preload color
        fac.getColorAsync(img)
          .then(color => {
            // Store color data on the element
            tool.dataset.bgColor = color.hex + '20';
            tool.dataset.borderColor = color.hex + '80';
            tool.dataset.textColor = color.hex;
          })
          .catch(e => {
            console.log(e);
          });

        // Add hover event listeners
        tool.addEventListener('mouseenter', () => {
          if (tool.dataset.bgColor) {
            tool.style.backgroundColor = tool.dataset.bgColor;
            tool.style.borderColor = tool.dataset.borderColor;
            label.style.color = tool.dataset.textColor;
          }
        });

        tool.addEventListener('mouseleave', () => {
          tool.style.backgroundColor = '';
          tool.style.borderColor = '';
          label.style.color = '';
        });

        // Intersection Observer to trigger fade-in when the element is in view
        const observer = new IntersectionObserver(entries => {
          entries.forEach(entry => {
            if (entry.isIntersecting) {
              entry.target.classList.add('visible');
            }
          });
        }, {
          threshold: 0.20,
        });

        observer.observe(tool);
      });
    });
  }
}
</script>

<style scoped>
.tool-item {
  padding: 1rem;
  border-radius: 0.5rem;
  border: 1px solid rgba(31, 41, 55, 0.5);
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  transition: all 0.3s ease;
  opacity: 0;
  transform: translateY(20px);
  transition: all 0.5s ease, transform 0.5s ease;
}

.tool-item.visible {
  opacity: 1;
  transform: translateY(0);
}
</style>