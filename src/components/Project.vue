<script setup lang="ts">
import { ref, onMounted } from 'vue';

const projects = ref([
  {
    id: 'pipeline',
    title: 'Pipeline Builder',
    description: 'Developed a sophisticated workflow builder featuring drag-and-drop node creation, dynamic pipeline logic, and backend DAG validation.',
    link: 'https://github.com',
    type: 'GITHUB',
    theme: 'blue-clouds'
  },
  {
    id: 'racan-ai',
    title: 'Racan AI',
    description: 'Expanded complex REST APIs for real-time data processing and interactive visualization.',
    link: 'https://racan-ai.vercel.app/about',
    type: 'MY WORK',
    theme: 'yellow-grid'
  },
  {
    id: 'events',
    title: 'Event Booking Platform',
    description: 'Improved a full-stack system capable of handling 1,000+ concurrent user sessions during peak booking hours.',
    link: 'https://racan-events-1.onrender.com/',
    type: 'APP LINK',
    theme: 'green-grid'
  }
]);

const revealed = ref(false);
onMounted(() => {
  setTimeout(() => (revealed.value = true), 100);
});
</script>

<template>
  <section class="projects-section" id="projects">
    <div class="projects-container">
      <div class="bento-grid">
        <!-- Pipeline Builder -->
        <div class="project-card pipeline-card" :class="{ revealed }">
           <div class="illustration-area clouds">
              <div class="cloud c1"></div>
              <div class="cloud c2"></div>
              <div class="cloud c3"></div>
           </div>
           <div class="card-content">
              <h3>{{ projects[0].title }}</h3>
              <p>{{ projects[0].description }}</p>
              <a :href="projects[0].link" target="_blank" class="demo-btn">
                 Visit project <span class="arrow">→</span>
              </a>
           </div>
        </div>

        <!-- Racan AI -->
        <div class="project-card ai-card" :class="{ revealed }">
           <div class="illustration-area  grid-pattern yellow">
              <div class="sketch-person walking">
                 <!-- Simple SVG Icon placeholder that looks like a sketch -->
                 <svg width="80" height="80" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5">
                    <path d="M13 4v4l-3-1M7 21l3-4M17 21l-2-7 2-3M13 8l2 5M13 8c1 0 2-1 2-2s-1-2-2-2-2 1-2 2 1 2 2 2z"/>
                 </svg>
              </div>
           </div>
           <div class="card-content">
              <h3>{{ projects[1].title }}</h3>
              <p>{{ projects[1].description }}</p>
              <a :href="projects[1].link" target="_blank" class="demo-btn">
                 Visit project <span class="arrow">→</span>
              </a>
           </div>
        </div>

        <!-- Event Booking -->
        <div class="project-card events-card" :class="{ revealed }">
           <div class="card-layout-horizontal">
              <div class="card-content">
                <h3>{{ projects[2].title }}</h3>
                <p>{{ projects[2].description }}</p>
                <a :href="projects[2].link" target="_blank" class="demo-btn">
                   Visit project <span class="arrow">→</span>
                </a>
              </div>
              <div class="illustration-area grid-pattern green">
                  <div class="sketch-person working desktop-only">
                    <svg width="120" height="120" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1">
                       <rect x="4" y="10" width="16" height="10" rx="1"/>
                       <path d="M12 10V6M12 6c0-1 1-2 2-2s2 1 2 2-1 2-2 2-2-1-2-2z"/>
                       <path d="M8 20l-1 2M16 20l1 2"/>
                    </svg>
                  </div>
                  <div class="mobile-arrow-container">
                    <svg viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg" class="mobile-arrow">
                        <path d="M5 12H19M19 12L12 5M19 12L12 19" stroke="#121212" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
                    </svg>
                  </div>
              </div>
           </div>
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
.projects-section {
  background-color: #fdfbef; /* Creamy background from reference */
  padding: 100px 20px;
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
}

.projects-container {
  max-width: 1200px;
  width: 100%;
}

.bento-grid {
  display: grid;
  grid-template-columns: 1fr 1fr;
  grid-template-rows: auto auto;
  gap: 25px;
}

.project-card {
  background: white;
  border: 3px solid #000;
  border-radius: 32px;
  overflow: hidden;
  position: relative;
  display: flex;
  flex-direction: column;
  transition: transform 0.3s ease, box-shadow 0.3s ease;
  box-shadow: 0 8px 0 #000;
}

.project-card:hover {
  transform: translate(-4px, -4px);
  box-shadow: 12px 12px 0 #000;
}

/* Specific Themes */
.pipeline-card .illustration-area {
  background: linear-gradient(to bottom, #7dd3fc, #f0f9ff);
  height: 200px;
  position: relative;
}

.ai-card .illustration-area {
  background-color: #fef08a;
  height: 200px;
  background-image: 
    linear-gradient(#00000010 1px, transparent 1px),
    linear-gradient(90deg, #00000010 1px, transparent 1px);
  background-size: 20px 20px;
}

.events-card {
  grid-column: span 2;
}

.events-card .illustration-area {
  background-color: #bbf7d0;
  flex: 1;
  min-height: 250px;
  background-image: 
    linear-gradient(#00000010 1px, transparent 1px),
    linear-gradient(90deg, #00000010 1px, transparent 1px);
  background-size: 30px 30px;
}

.card-layout-horizontal {
  display: flex;
  align-items: center;
}

.card-layout-horizontal .card-content {
  flex: 1;
  padding: 40px;
}

.card-content {
  padding: 30px;
  z-index: 2;
}

.card-content h3 {
  font-size: 2rem;
  font-weight: 800;
  color: #000;
  margin-bottom: 15px;
  font-family: 'Outfit', sans-serif;
}

.card-content p {
  font-size: 1rem;
  line-height: 1.6;
  color: #4b5563;
  font-weight: 500;
}

/* Illustrations */
.clouds {
  display: flex;
  align-items: center;
  justify-content: center;
}

.cloud {
  background: white;
  height: 40px;
  width: 100px;
  border-radius: 50px;
  position: absolute;
  filter: blur(8px);
  opacity: 0.8;
  animation: floatCloud 8s infinite ease-in-out;
}

.c1 { top: 20%; left: 20%; }
.c2 { top: 50%; right: 10%; width: 140px; animation-delay: -2s; }
.c3 { bottom: 20%; left: 40%; width: 80px; animation-delay: -4s; }

@keyframes floatCloud {
  0%, 100% { transform: translateX(0); }
  50% { transform: translateX(20px); }
}

.sketch-person {
  position: absolute;
  bottom: 0;
  right: 20px;
  display: flex;
  align-items: center;
  justify-content: center;
  color: #000;
}

.working {
  right: 50px;
  bottom: 20px;
}

.mobile-arrow-container {
  display: none;
  width: 100%;
  height: 100%;
  justify-content: center;
  align-items: center;
}

.mobile-arrow {
  width: 50%;
  height: 50%;
  transform: rotate(-45deg);
}

/* Button */
.demo-btn {
  display: inline-flex;
  align-items: center;
  gap: 10px;
  background: #ffffff;
  color: #150144;
  padding: 12px 24px;
  border-radius: 60px;
  text-decoration: none;
  font-weight: 800;
  margin-top: 25px;
  transition: transform 0.2s;
  border: 1px solid #150144;
}

.demo-btn:hover {
  transform: scale(1.05);
}

.arrow {
  transition: transform 0.2s;
}

.demo-btn:hover .arrow {
  transform: translateX(5px);
}

@media (max-width: 800px) {
  .projects-section {
    padding: 60px 15px;
  }
  .bento-grid {
    grid-template-columns: 1fr;
    gap: 20px;
  }
  .events-card {
    grid-column: span 1;
  }
  .card-layout-horizontal {
    flex-direction: column;
  }
  .card-content {
    padding: 20px;
  }
  .card-content h3 {
    font-size: 1.6rem;
  }
  .card-content p {
    font-size: 0.95rem;
  }
  .pipeline-card .illustration-area, .ai-card .illustration-area {
    height: 160px;
  }
  .events-card .illustration-area {
    min-height: 200px;
    background-color: #38ef7d; /* Vibrant Green from footer */
  }
  .desktop-only {
    display: none;
  }
  .mobile-arrow-container {
    display: flex;
  }
}
</style>
