<script setup lang="ts">
// Professional Skills Marquee Component
</script>

<template>
  <div class="marquee-container">
    <div class="marquee-wrapper">
      <div class="marquee-content">
        <!-- Group 1 -->
        <div class="skill-tag"><i class="fa-brands fa-react"></i> React</div>
        <div class="skill-tag"><i class="fa-brands fa-vuejs"></i> Vue.js</div>
        <div class="skill-tag"><i class="fa-brands fa-js"></i> JavaScript</div>
        <div class="skill-tag"><i class="fa-brands fa-node-js"></i> Node.js</div>
        <div class="skill-tag"><i class="fa-brands fa-python"></i> Python</div>
        <div class="skill-tag"><i class="fa-brands fa-figma"></i> Figma</div>
        <div class="skill-tag"><i class="fa-brands fa-html5"></i> HTML5</div>
        <div class="skill-tag"><i class="fa-brands fa-css3-alt"></i> CSS3</div>
        <div class="skill-tag"><i class="fa-solid fa-database"></i> MongoDB</div>
        <div class="skill-tag"><i class="fa-solid fa-server"></i> Express</div>
        
        <!-- Duplicate for seamless loop -->
        <div class="skill-tag"><i class="fa-brands fa-react"></i> React</div>
        <div class="skill-tag"><i class="fa-brands fa-vuejs"></i> Vue.js</div>
        <div class="skill-tag"><i class="fa-brands fa-js"></i> JavaScript</div>
        <div class="skill-tag"><i class="fa-brands fa-node-js"></i> Node.js</div>
        <div class="skill-tag"><i class="fa-brands fa-python"></i> Python</div>
        <div class="skill-tag"><i class="fa-brands fa-figma"></i> Figma</div>
        <div class="skill-tag"><i class="fa-brands fa-html5"></i> HTML5</div>
        <div class="skill-tag"><i class="fa-brands fa-css3-alt"></i> CSS3</div>
        <div class="skill-tag"><i class="fa-solid fa-database"></i> MongoDB</div>
        <div class="skill-tag"><i class="fa-solid fa-server"></i> Express</div>
      </div>
    </div>
  </div>
</template>

<style scoped>
.marquee-container {
  width: 100%;
  max-width: 100vw;
  height: 100%;
  background: white;
  padding: 2rem 0;
  overflow: hidden;
  border-bottom: 2px solid #eee;
    border: #000000 2px solid;
    border-left: none;
    border-right: none;
    bottom: 10px;
}

.marquee-wrapper {
  display: flex;
  width: 100%;
}

.marquee-content {
  display: flex;
  gap: 3rem;
  animation: scroll 30s linear infinite;
  padding-left: 3rem;
}

.skill-tag {
  display: flex;
  align-items: center;
  gap: 10px;
  font-size: 1.2rem;
  font-weight: 600;
  color: #333;
  white-space: nowrap;
  padding: 10px 20px;
  background: #f9f9f9;
  border-radius: 50px;
  border: 1px solid #ddd;
  transition: all 0.3s ease;
}

.skill-tag i {
  font-size: 1.4rem;
  color: #6366f1;
}

.skill-tag:hover {
  background: #6366f1;
  color: white;
  border-color: #6366f1;
  transform: translateY(-2px);
}

.skill-tag:hover i {
  color: white;
}

@keyframes scroll {
  0% {
    transform: translateX(0);
  }
  100% {
    transform: translateX(-50%);
  }
}

.marquee-container:hover .marquee-content {
  animation-play-state: paused;
}

@media (max-width: 768px) {
  .skill-tag {
    font-size: 1rem;
    padding: 8px 15px;
  }
  .marquee-content {
    gap: 1.5rem;
    animation-duration: 20s;
  }
}
</style>