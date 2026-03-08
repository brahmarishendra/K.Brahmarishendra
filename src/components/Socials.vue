<script setup lang="ts">
import { ref, onMounted, onUnmounted } from 'vue';

const profileData = ref({
  name: 'Kesari Brahmarishendra',
  pronouns: 'He/Him',
  role: 'UI UX designer | Web front-end',
  bio: 'DB: Mongo DB | Nodejs & express | Graphic designer | CRM (Salesforce & HubSpot) Customer Success Enthusiast, I am passionate about Startups and company growth 🚀💡',
  avatar: 'https://media.licdn.com/dms/image/v2/D4D03AQF1ZSz9Ex1Qtg/profile-displayphoto-scale_400_400/B4DZvLeVkPI0Ag-/0/1768645288721?e=2147483647&v=beta&t=tAhocZkCbg23IBs9Da5bp2Agw-ckwbuS6LAAi3ODSWs',
  location: 'Halol, Gujarat, India',
  connections: '500+',
  email: 'brahmarishi868@gmail.com',
  linkedin: 'https://www.linkedin.com/in/kesari-brahmarishendra-8a54b0260/',
  twitter: 'https://twitter.com/comicboyssSSst1/status/1699746513428377635',
  github: 'https://github.com/brahmarishendra'
});

// Eye Tracking Logic
const leftPupil = ref<HTMLElement | null>(null);
const rightPupil = ref<HTMLElement | null>(null);

const handleMouseMove = (e: MouseEvent) => {
  const pupils = [leftPupil.value, rightPupil.value];
  pupils.forEach(pupil => {
    if (!pupil) return;
    const rect = pupil.getBoundingClientRect();
    const x = rect.left + rect.width / 2;
    const y = rect.top + rect.height / 2;
    
    // Calculate distance between mouse and pupil center
    const dx = e.clientX - x;
    const dy = e.clientY - y;
    const angle = Math.atan2(dy, dx);
    
    // Max movement distance for the pupil within the white eye area
    const maxMove = 3; 
    const moveX = Math.cos(angle) * maxMove;
    const moveY = Math.sin(angle) * maxMove;
    
    pupil.style.transform = `translate(${moveX}px, ${moveY}px)`;
  });
};

onMounted(() => {
  window.addEventListener('mousemove', handleMouseMove);
});

onUnmounted(() => {
  window.removeEventListener('mousemove', handleMouseMove);
});
</script>

<template>
  <section class="socials-section" id="socials">
    <!-- Left Column -->
    <div class="content-side">
      <div class="text-container">
        <div class="social-links-minimal">
           <a :href="profileData.twitter" target="_blank" class="x-link">
              <i class="fa-brands fa-x-twitter"></i> Twitter
           </a>
        </div>
        <h2>Let's Connect and <br><span>Build Together</span></h2>
        <p class="hero-sub">I'm always open to discussing new projects, creative ideas, or startups. Let's create something exceptional.</p>
        
        <div class="btn-stack">
          <div class="btn-layer layer-1"></div>
          <div class="btn-layer layer-2"></div>
          <a :href="`mailto:${profileData.email}`" class="connect-btn">
            Send Email <span class="arrow">→</span>
          </a>
        </div>
      </div>
    </div>

    <!-- Right Side -->
    <div class="visual-side">
      <div class="browser-window">
        <div class="window-header">
          <div class="dots">
            <span class="dot red"></span>
            <span class="dot yellow"></span>
            <span class="dot green"></span>
          </div>
        </div>

        <div class="window-body">
          <div class="profile-header">
            <div class="avatar-container">
              <img :src="profileData.avatar" alt="Profile">
              <div class="social-icon linked">
                 <i class="fa-brands fa-linkedin-in"></i>
              </div>
            </div>
            <div class="profile-info">
              <h3>{{ profileData.name }} <span class="pronouns">{{ profileData.pronouns }}</span></h3>
              <p class="role-text">{{ profileData.role }}</p>
            </div>
          </div>

          <div class="bio-content">
            <p>{{ profileData.bio }}</p>
          </div>

          <div class="stats-row">
            <div class="stat-pill">
              <i class="fa-solid fa-users"></i>
              <span>{{ profileData.connections }}</span>
            </div>
            <div class="stat-pill github">
              <a :href="profileData.github" target="_blank">
                <i class="fa-brands fa-github"></i>
                <span>GitHub</span>
              </a>
            </div>
            <div class="stat-pill">
              <i class="fa-solid fa-location-dot"></i>
              <span>{{ profileData.location }}</span>
            </div>
          </div>

          <div class="window-actions">
            <a :href="profileData.linkedin" target="_blank" class="btn secondary">Follow Me</a>
            <a :href="`mailto:${profileData.email}`" class="btn primary">Send Message <i class="fa-solid fa-paper-plane"></i></a>
          </div>
        </div>
      </div>

      <!-- Panda Illustration -->
      <div class="panda-container">
         <div class="panda-head">
            <div class="ear left"></div>
            <div class="ear right"></div>
            <div class="eye-patch left">
               <div class="eye">
                  <div class="pupil" ref="leftPupil"></div>
               </div>
            </div>
            <div class="eye-patch right">
               <div class="eye">
                  <div class="pupil" ref="rightPupil"></div>
               </div>
            </div>
            <div class="nose"></div>
            <div class="mouth"></div>
         </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
.socials-section {
  display: grid;
  grid-template-columns: 1fr 1.2fr;
  min-height: 85vh;
  font-family: 'Inter', sans-serif;
}

.content-side {
  background-color: #ede9fe;
  display: flex;
  align-items: center;
  justify-content: center;
  padding: 60px;
}

.text-container {
  max-width: 500px;
}

.social-links-minimal {
  margin-bottom: 20px;
}

.x-link {
  text-decoration: none;
  color: #000;
  font-weight: 800;
  font-size: 0.9rem;
  display: flex;
  align-items: center;
  gap: 8px;
  transition: opacity 0.2s;
}

.x-link:hover { opacity: 0.7; }

.text-container h2 {
  font-size: 3rem;
  font-weight: 900;
  color: #000;
  line-height: 1.1;
  margin-bottom: 20px;
  font-family: 'Outfit', sans-serif;
}

.text-container h2 span { color: #6d28d9; }

.hero-sub {
  font-size: 1.1rem;
  color: #4b5563;
  margin-bottom: 50px;
  line-height: 1.6;
}

.btn-stack { position: relative; display: inline-block; }
.btn-layer { position: absolute; top: 0; left: 0; width: 100%; height: 100%; border: 2px solid #000; border-radius: 4px; }
.layer-1 { background-color: #c4b5fd; transform: translate(6px, 6px); }
.layer-2 { background-color: #a78bfa; transform: translate(12px, 12px); }

.connect-btn {
  position: relative;
  z-index: 2;
  display: inline-flex;
  align-items: center;
  gap: 12px;
  background: #000;
  color: #fff;
  padding: 16px 40px;
  border-radius: 4px;
  text-decoration: none;
  font-weight: 800;
  font-size: 1.1rem;
  border: 2px solid #000;
  transition: transform 0.1s ease;
}

.connect-btn .layer-1 {
  transition: transformx 0.1s ease;
}

.connect-btn:active { transform: translate(6px, 6px); }
.arrow { transition: transform 0.2s; }
.connect-btn:hover .arrow { transform: translateX(6px); }

.visual-side {
  background-color: #4f46e5;
  background-image: 
    linear-gradient(#ffffff08 1px, transparent 1px),
    linear-gradient(90deg, #ffffff08 1px, transparent 1px);
  background-size: 30px 30px;
  display: flex;
  align-items: center;
  justify-content: center;
  position: relative;
  padding: 40px;
}

.browser-window {
  background: white;
  border: 3px solid #000;
  border-radius: 12px;
  width: 100%;
  max-width: 500px;
  box-shadow: 12px 12px 0 #000;
  z-index: 2;
  overflow: hidden;
  transition: transform 0.3s ease;
}

.visual-side:hover .browser-window {
  transform: translateY(-5px);
}

.window-header {
  border-bottom: 3px solid #000;
  padding: 10px 15px;
  background: #fdfbf7;
}

.dots { display: flex; gap: 6px; }
.dot { width: 10px; height: 10px; border-radius: 50%; border: 1.5px solid #000; }
.dot.red { background: #ff5f56; }
.dot.yellow { background: #ffbd2e; }
.dot.green { background: #27c93f; }

.window-body { padding: 30px; }

.profile-header {
  display: flex;
  align-items: center;
  gap: 20px;
  margin-bottom: 25px;
}

.avatar-container { position: relative; }
.avatar-container img {
  width: 80px;
  height: 80px;
  border-radius: 50%;
  border: 3px solid #000;
  object-fit: cover;
}

.social-icon {
  position: absolute;
  bottom: 0;
  right: 0;
  width: 26px;
  height: 26px;
  background: #0077b5;
  color: white;
  border-radius: 50%;
  border: 2px solid #000;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 0.7rem;
}

.profile-info h3 {
  font-size: 1.4rem;
  font-weight: 800;
  margin: 0;
  color: #000;
  display: flex;
  align-items: center;
  gap: 8px;
}

.pronouns { font-size: 0.8rem; color: #888; font-weight: 600; }
.role-text { font-size: 0.9rem; color: #4b5563; font-weight: 700; margin-top: 2px; }

.bio-content {
  background: #fdfbef;
  border: 2px solid #000;
  padding: 15px;
  border-radius: 8px;
  margin-bottom: 25px;
}

.bio-content p {
  font-size: 0.85rem;
  line-height: 1.5;
  color: #374151;
  font-weight: 500;
  margin: 0;
}

.stats-row {
  display: flex;
  gap: 10px;
  margin-bottom: 25px;
  flex-wrap: wrap;
}

.stat-pill {
  background: white;
  border: 2px solid #000;
  padding: 5px 12px;
  border-radius: 50px;
  display: flex;
  align-items: center;
  gap: 8px;
  font-size: 0.75rem;
  font-weight: 800;
}

.stat-pill.github a { text-decoration: none; color: inherit; display: flex; align-items: center; gap: 8px; }

.window-actions {
  display: grid;
  grid-template-columns: 1fr 1.5fr;
  gap: 12px;
}

.btn {
  padding: 12px;
  border-radius: 8px;
  font-weight: 800;
  font-size: 0.85rem;
  cursor: pointer;
  border: 3px solid #000;
  transition: transform 0.1s ease;
  text-decoration: none;
  text-align: center;
}

.btn.primary { background: #4f46e5; color: white; display: flex; align-items: center; justify-content: center; gap: 8px; }
.btn.secondary { background: white; color: #000; }
.btn:hover { transform: translateY(-2px); }

/* Panda Illustration */
.panda-container {
  position: absolute;
  top: 10%;
  left: 20%;
  z-index: 3;
  opacity: 0;
  transform: scale(0.6) translateY(20px);
  transition: all 0.5s cubic-bezier(0.175, 0.885, 0.32, 1.275);
  pointer-events: none;
}

.visual-side:hover .panda-container {
  opacity: 1;
  transform: scale(0.6) translateY(0);
}

.panda-head {
  width: 90px;
  height: 80px;
  background: white;
  border: 3px solid #000;
  border-radius: 40px;
  position: relative;
}

.ear {
  width: 25px;
  height: 25px;
  background: #000;
  border-radius: 50%;
  position: absolute;
  top: -10px;
}

.ear.left { left: 0; }
.ear.right { right: 0; }

.eye-patch {
  width: 28px;
  height: 32px;
  background: #000;
  border-radius: 12px;
  position: absolute;
  top: 15px;
}

.eye-patch.left { left: 12px; transform: rotate(10deg); }
.eye-patch.right { right: 12px; transform: rotate(-10deg); }

.eye {
  width: 12px;
  height: 12px;
  background: white;
  border-radius: 50%;
  position: absolute;
  top: 8px;
  left: 8px;
  display: flex;
  align-items: center;
  justify-content: center;
  will-change: transform;
}

.pupil {
  width: 6px;
  height: 6px;
  background: #000;
  border-radius: 50%;
}

.nose {
  width: 12px;
  height: 8px;
  background: #000;
  border-radius: 50%;
  position: absolute;
  bottom: 25px;
  left: 50%;
  transform: translateX(-50%);
}

.mouth {
  width: 14px;
  height: 6px;
  border-bottom: 2px solid #000;
  border-radius: 50%;
  position: absolute;
  bottom: 15px;
  left: 50%;
  transform: translateX(-50%);
}

@media (max-width: 1000px) {
  .socials-section { grid-template-columns: 1fr; }
  .content-side { padding: 40px 20px; text-align: center; }
  .text-container h2 { font-size: 2.2rem; }
  .hero-sub { margin-bottom: 30px; font-size: 1rem; }
  .visual-side { padding: 40px 15px; }
  .browser-window { max-width: 100%; box-shadow: 8px 8px 0 #000; }
  .window-body { padding: 20px; }
  .profile-header { flex-direction: column; text-align: center; }
  .avatar-container img { width: 70px; height: 70px; }
  .window-actions { grid-template-columns: 1fr; }
  .panda-container { display: none; }
}

@media (max-width: 480px) {
  .text-container h2 { font-size: 1.8rem; }
  .connect-btn { padding: 14px 30px; font-size: 1rem; }
}
</style>
