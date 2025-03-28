<template>
  <div class="w-screen h-screen bg-black border fixed">
    <div ref="spaceContainer" class="space-container"></div>
  </div>
</template>

<script>
import Top from "./Top.vue";

export default {
  data() {
    return {
      stars: [],
      starCount: 650,
      maxDepth: 1500,
      speedFactor: 7,
      animationFrameId: null
    };
  },
  components: {
    Top
  },
  mounted() {

    // Create star animation
    this.initStars();
    this.animateStars();
  },
  beforeUnmount() {
    // Clean up animation frame when component is destroyed
    if (this.animationFrameId) {
      cancelAnimationFrame(this.animationFrameId);
    }
  },
  methods: {
    initStars() {
      const spaceContainer = this.$refs.spaceContainer;
      
      // Create stars
      for (let i = 0; i < this.starCount; i++) {
        const star = document.createElement('div');
        star.classList.add('star');
        this.resetStar(star, true);
        spaceContainer.appendChild(star);
        this.stars.push({
          element: star,
          x: parseFloat(star.style.left),
          y: parseFloat(star.style.top),
          z: parseFloat(star.dataset.z)
        });
      }
    },
    resetStar(star, initial = false) {
      // Set random x and y positions
      const x = Math.random() * 100;
      const y = Math.random() * 100;
      
      star.style.left = `${x}%`;
      star.style.top = `${y}%`;
      
      // Set initial z position (depth)
      const z = initial ? Math.random() * this.maxDepth : this.maxDepth;
      star.dataset.z = z;
      
      // Set initial size and opacity based on depth
      this.updateStarAppearance(star, z);
    },
    updateStarAppearance(star, z) {
      // Calculate size based on z position (closer = bigger)
      const size = Math.max(0.3, (this.maxDepth - z) / 450);
      
      // Calculate opacity based on z position (closer = brighter)
      const opacity = Math.min(1, Math.max(0.2, (this.maxDepth - z) / this.maxDepth));
      
      // Apply the calculated values
      star.style.width = `${size}px`;
      star.style.height = `${size}px`;
      star.style.opacity = opacity;
      
      // Create trail effect for stars that are close
      if (z < 300) {
        const trailLength = Math.min(15, (300 - z) / 20);
        star.style.boxShadow = `0 0 ${trailLength}px 1px rgba(255, 255, 255, ${opacity * 0.5})`;
      } else {
        star.style.boxShadow = 'none';
      }
    },
    animateStars() {
      for (let i = 0; i < this.stars.length; i++) {
        const star = this.stars[i];
        
        // Update z position (move closer)
        let z = parseFloat(star.element.dataset.z) - this.speedFactor;
        
        // If the star is too close, reset it
        if (z <= 0) {
          this.resetStar(star.element);
          this.stars[i].x = parseFloat(star.element.style.left);
          this.stars[i].y = parseFloat(star.element.style.top);
          this.stars[i].z = this.maxDepth;
        } else {
          star.element.dataset.z = z;
          
          // Update visual appearance based on new z position
          this.updateStarAppearance(star.element, z);
          
          // Calculate new x and y based on perspective (parallax effect)
          const scale = this.maxDepth / (z || 1);
          const centerX = 50;
          const centerY = 50;
          
          const newX = centerX + (star.x - centerX) * scale;
          const newY = centerY + (star.y - centerY) * scale;
          
          star.element.style.left = `${newX}%`;
          star.element.style.top = `${newY}%`;
        }
      }
      
      this.animationFrameId = requestAnimationFrame(this.animateStars);
    }
  }
};
</script>

<style>
.space-container {
  position: absolute;
  width: 100%;
  height: 100%;
  perspective: 1000px;
  overflow: hidden;
}

.star {
  position: absolute;
  width: 1px;
  height: 1px;
  background-color: #ffffff;
  border-radius: 50%;
  transform-style: preserve-3d;
  z-index: 10;
}
</style>
