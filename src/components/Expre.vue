<script setup lang="ts">
import { onMounted, ref } from 'vue';

interface Experience {
  id: number;
  company: string;
  role: string;
  date: string;
  location: string;
  tags: string[];
  description: string;
  color: string;
  metric?: string;
  visual?: string; // Icon or pattern type
  link?: string;
}

const experiences = ref<Experience[]>([
  {
    id: 1,
    company: 'DreamX Store',
    role: 'UI/UX & UI Developer',
    date: 'MARCH 2025 - OCTOBER 2025',
    location: 'Remote',
    tags: ['Full-time', 'Development', 'Design'],
    description: 'Spearheaded end-to-end design and frontend for high-traffic e-commerce interfaces. Improved load speeds by 30% and boosted engagement by 20%.',
    color: '#FF4D00', // Vibrant Orange
    metric: '30% SPEED BOOST',
    visual: 'dots',
    link: 'https://dream-x-info.vercel.app/'
  },
  {
    id: 2,
    company: 'Prahan Soft',
    role: 'Frontend Web Developer Intern',
    date: 'MARCH 2023 – MAY 2023',
    location: 'Remote/On-site',
    tags: ['Internship', 'Engineering'],
    description: 'Engineered responsive web apps improving retention by 15%. Automated placement processes for TPO AI, reducing administrative workload by 40%.',
    color: '#2B5CFB', // Shardian Blue
    metric: '40% WORKLOAD REDUCTION',
    visual: 'grid'
  },
  {
    id: 3,
    company: 'Health Pulse Connect',
    role: 'Web UI Designer Intern',
    date: 'AUGUST 2024 – SEPTEMBER 2024',
    location: 'Vadodara, India',
    tags: ['Internship', 'UI/UX Design'],
    description: 'Designed intuitive diagnostic UI for 50+ hospital staff members. Refined digital interfaces resulting in a measurable 12% improvement in accessibility.',
    color: '#A3FF00', // Neon Green
    metric: '12% ACCESSIBILITY GAIN',
    visual: 'waves',
    link: 'https://www.figma.com/community/file/1471491722709765043/hpc-web-ui'
  }
]);

const cardsRevealed = ref<boolean[]>(new Array(experiences.value.length).fill(false));
const cardRefs = ref<HTMLElement[]>([]);

const setCardRef = (el: any, index: number) => {
  if (el) cardRefs.value[index] = el;
};

onMounted(() => {
  const observer = new IntersectionObserver((entries) => {
    entries.forEach((entry) => {
      if (entry.isIntersecting) {
        const index = cardRefs.value.indexOf(entry.target as HTMLElement);
        if (index !== -1) {
          cardsRevealed.value[index] = true;
          observer.unobserve(entry.target);
        }
      }
    });
  }, { threshold: 0.1 });

  cardRefs.value.forEach((card) => {
    observer.observe(card);
  });
});
</script>

<template>
  <section class="experience-gallery" id="experience">
    <div class="gallery-container">
      <header class="gallery-header">
        <p class="eyebrow">PROFESSIONAL JOURNEY</p>
        <h2>Work Experience</h2>
      </header>

      <div class="experience-grid">
        <div 
          v-for="(exp, index) in experiences" 
          :key="exp.id" 
          class="shardian-card"
          :class="{ 'revealed': cardsRevealed[index] }"
          :ref="el => setCardRef(el, index)"
          :style="{ transitionDelay: `${index * 0.15}s` }"
        >
          <!-- Card Header Visual -->
          <div class="card-visual" :style="{ backgroundColor: '#000' }">
            <div class="visual-pattern" :class="exp.visual"></div>
            <div class="brand-tag">
               <span class="logo-symbol">∆</span>
               <span class="company-name">{{ exp.company }}</span>
            </div>
            <div class="impact-pill" v-if="exp.metric">{{ exp.metric }}</div>
          </div>

          <!-- Card Body -->
          <div class="card-body">
            <div class="card-meta">
              <span class="meta-date">{{ exp.date }}</span>
              <div class="meta-tags">
                <span v-for="tag in exp.tags" :key="tag" class="pill-tag">{{ tag }}</span>
              </div>
            </div>

            <h3 class="card-title">{{ exp.role }}</h3>
            <p class="card-description">{{ exp.description }}</p>

            <a v-if="exp.link" :href="exp.link" target="_blank" class="read-more">
              EXPLORE WORK <span>→</span>
            </a>
            <span v-else class="read-more static">CASE STUDY COMING SOON</span>
          </div>
        </div>
      </div>

      <!-- Mobile Only View More Button -->
      <div class="mobile-action">
          <a href="#projects" class="mobile-btn">
              Next Projects <i class="fa-solid fa-arrow-right"></i>
          </a>
      </div>
    </div>
  </section>
</template>

<style scoped>
.experience-gallery {
  background-color: #2b5cfb; /* Shardian Vibrant Blue */
  padding: 120px 20px;
  min-height: 100vh;
  display: flex;
  align-items: center;
  justify-content: center;
  font-family: 'Inter', sans-serif;
}

.gallery-container {
  max-width: 1300px;
  width: 100%;
}

.gallery-header {
  margin-bottom: 60px;
  text-align: center;
}

.eyebrow {
  color: rgba(255, 255, 255, 0.8);
  font-size: 0.9rem;
  font-weight: 800;
  letter-spacing: 0.2em;
  margin-bottom: 10px;
}

.gallery-header h2 {
  font-size: 4rem;
  font-weight: 900;
  color: #fff;
  margin: 0;
  font-family: 'Outfit', sans-serif;
  letter-spacing: -2px;
}

.experience-grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 30px;
}

/* Card Styling */
.shardian-card {
  background: white;
  border-radius: 4px;
  overflow: hidden;
  box-shadow: 0 20px 40px rgba(0, 0, 0, 0.1);
  display: flex;
  flex-direction: column;
  
  /* Reveal Animation States */
  opacity: 0;
  transform: translateY(40px);
  transition: opacity 0.8s ease, transform 0.8s cubic-bezier(0.17, 0.67, 0.83, 0.67), box-shadow 0.4s ease;
}

.shardian-card.revealed {
  opacity: 1;
  transform: translateY(0);
}

.shardian-card:hover {
  transform: translateY(-12px);
  box-shadow: 0 40px 80px rgba(0, 0, 0, 0.2);
}

.card-visual {
  height: 220px;
  position: relative;
  overflow: hidden;
  display: flex;
  align-items: center;
  justify-content: center;
}

.visual-pattern {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  opacity: 0.2;
}

/* Pattern Variations */
.dots {
  background-image: radial-gradient(rgba(255,255,255,0.4) 1px, transparent 1px);
  background-size: 20px 20px;
}

.grid {
  background-image: linear-gradient(rgba(255,255,255,0.1) 1px, transparent 1px),
                    linear-gradient(90deg, rgba(255,255,255,0.1) 1px, transparent 1px);
  background-size: 30px 30px;
}

.waves {
  background: repeating-linear-gradient(45deg, transparent, transparent 10px, rgba(255,255,255,0.05) 10px, rgba(255,255,255,0.05) 20px);
}

.brand-tag {
  z-index: 2;
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 10px;
}

.logo-symbol {
  font-size: 2.5rem;
  font-weight: 900;
  color: #fff;
}

.company-name {
  font-size: 1.2rem;
  font-weight: 800;
  color: #fff;
  letter-spacing: 1px;
  text-transform: uppercase;
}

.impact-pill {
  position: absolute;
  top: 20px;
  left: 20px;
  background: white;
  padding: 6px 14px;
  border-radius: 50px;
  font-size: 0.75rem;
  font-weight: 900;
  color: #000;
  box-shadow: 0 4px 10px rgba(0,0,0,0.2);
}

.card-body {
  padding: 35px;
  flex: 1;
  display: flex;
  flex-direction: column;
}

.card-meta {
  margin-bottom: 20px;
}

.meta-date {
  display: block;
  font-size: 0.8rem;
  font-weight: 800;
  color: #888;
  margin-bottom: 12px;
  text-transform: uppercase;
}

.meta-tags {
  display: flex;
  flex-wrap: wrap;
  gap: 8px;
}

.pill-tag {
  border: 1px solid #eee;
  padding: 4px 12px;
  border-radius: 50px;
  font-size: 0.75rem;
  font-weight: 700;
  color: #666;
  text-transform: uppercase;
}

.card-title {
  font-size: 1.8rem;
  font-weight: 900;
  color: #000;
  margin: 0 0 15px 0;
  line-height: 1.2;
  font-family: 'Outfit', sans-serif;
}

.card-description {
  font-size: 1rem;
  line-height: 1.6;
  color: #555;
  margin-bottom: 30px;
  flex: 1;
}

.read-more {
  font-size: 0.85rem;
  font-weight: 900;
  color: #2b5cfb;
  text-decoration: none;
  display: flex;
  align-items: center;
  gap: 8px;
  transition: gap 0.3s;
}

.read-more.static {
  color: #bbb;
}

.read-more:not(.static):hover {
  gap: 15px;
}

/* Responsive */
@media (max-width: 1200px) {
  .experience-grid {
    grid-template-columns: repeat(2, 1fr);
  }
}

@media (max-width: 800px) {
  .experience-gallery {
    padding: 60px 0; /* Remove side padding to allow full-width scroll */
  }

  .gallery-header {
    padding: 0 20px;
    margin-bottom: 40px;
  }

  .gallery-header h2 {
    font-size: 2.2rem;
    letter-spacing: -1px;
  }

  .experience-grid {
    display: flex;
    overflow-x: auto;
    padding: 20px;
    gap: 20px;
    scroll-snap-type: x mandatory;
    -webkit-overflow-scrolling: touch;
    scrollbar-width: none; /* Hide scrollbar for clean look */
  }

  .experience-grid::-webkit-scrollbar {
    display: none;
  }

    .shardian-card {
    min-width: 85vw;
    scroll-snap-align: center;
  }

  /* Mobile Only Action Button */
  .mobile-action {
    display: flex;
    justify-content: center;
    margin-top: 40px;
    padding: 0 20px;
  }

  .mobile-btn {
    background-color: #0d0d21;
    color: white;
    padding: 1rem 2rem;
    border-radius: 50px;
    font-size: 1.1rem;
    font-weight: 700;
    display: flex;
    align-items: center;
    gap: 12px;
    text-decoration: none;
    border: 1.5px solid #0d0d21;
    transition: all 0.2s ease;
    width: 100%;
    justify-content: center;
    box-shadow: 4px 4px 0 rgba(0,0,0,0.2);
  }

  .mobile-btn:active {
    transform: translate(2px, 2px);
    box-shadow: 0 0 0 rgba(0,0,0,0.2);
  }
}

/* Hide mobile action on desktop */
@media (min-width: 801px) {
  .mobile-action {
    display: none;
  }
}
</style>
