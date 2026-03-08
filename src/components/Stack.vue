<script setup lang="ts">
import { ref, onMounted, onUnmounted } from 'vue';

const props = defineProps({
    heading: {
        type: String,
        required: false,
        default: 'My Tech Stack'
    }
});

const scrollContainer = ref<HTMLElement | null>(null);
const horizontalTrack = ref<HTMLElement | null>(null);
const scrollProgress = ref(0);

const slides = ref<HTMLElement[]>([]);
const setSlideRef = (el: any, index: number) => {
    if (el) slides.value[index] = el;
};

const handleScroll = () => {
    if (!scrollContainer.value || !horizontalTrack.value) return;
    
    const containerTop = scrollContainer.value.offsetTop;
    const containerHeight = scrollContainer.value.offsetHeight;
    const windowHeight = window.innerHeight;
    const scrollTop = window.pageYOffset;
    
    // Calculate progress within the sticky section
    let progress = (scrollTop - containerTop) / (containerHeight - windowHeight);
    progress = Math.max(0   , Math.min(1, progress));
    
    scrollProgress.value = progress;
};

onMounted(() => {
    window.addEventListener('scroll', handleScroll);
    handleScroll();

    // Intersection Observer for Reveal Animation
    const observer = new IntersectionObserver((entries) => {
        entries.forEach(entry => {
            if (entry.isIntersecting) {
                entry.target.classList.add('revealed');
            }
        });
    }, { 
        threshold: 0.05, // Lower threshold for better reliability
        rootMargin: '50px' // Start revealing slightly before they hit the viewport
    });

    // Small delay to ensure all refs are fully populated
    setTimeout(() => {
        slides.value.forEach(slide => {
            if (slide) observer.observe(slide);
        });
        
        // Fallback: Check if the first slide is already visible
        if (slides.value[0]) {
            slides.value[0].classList.add('revealed');
        }
    }, 100);
});

onUnmounted(() => {
    window.removeEventListener('scroll', handleScroll);
});
</script>

<template>
    <div class="sticky-parent" ref="scrollContainer">
        <div class="sticky-child">
            <!-- Grass Illustration Background -->
            <div class="grass-bg"></div>
            
            <h1 class="section-title">{{ heading }}</h1>
            
            <div class="horizontal-track" ref="horizontalTrack" :style="{ transform: `translateX(-${scrollProgress * 260}vw)` }">
                
                <!-- Slide 1: Backend -->
                <div class="skill-slide" :ref="el => setSlideRef(el, 0)">
                    <div class="slide-info">
                        <div class="badge">Backend Engineering</div>
                        <h2>The engine that <br><span>powers the experience.</span></h2>
                        <p>I build <strong>architectural foundations</strong> that are as solid as a mountain but as flexible as water. Scalable APIs, efficient database design, and <strong>robust logic</strong> are my specialties.</p>
                        <div class="hand-drawn-arrow">
                             <svg width="60" height="40" viewBox="0 0 60 40"><path d="M10,10 Q30,5 50,30 M50,30 L40,25 M50,30 L55,20" fill="none" stroke="#FFE227" stroke-width="2" /></svg>
                        </div>
                    </div>
                    <div class="polaroid-wrapper" style="--rotation: -2deg;">
                        <div class="tape-v2"></div>
                        <div class="polaroid-card">
                            <div class="card-inner">
                                <i class="fa-brands fa-node-js sticker node-sticker"></i>
                                <i class="fa-brands fa-python sticker py-sticker"></i>
                                <div class="skill-stack-list">
                                    <span>• Express.js & Middleware</span>
                                    <span>• MongoDB & MySQL</span>
                                    <span>• RESTful API Architecture</span>
                                    <span>• Server-side Logic</span>
                                </div>
                            </div>
                            <div class="polaroid-footer">
                                <span class="caption">BACKEND WIZARDRY!!</span>
                            </div>
                        </div>
                    </div>
                </div>

                <!-- Slide 2: Frontend -->
                <div class="skill-slide" :ref="el => setSlideRef(el, 1)">
                    <div class="slide-info">
                        <div class="badge">Frontend Artistry</div>
                        <h2>Designing for <br><span>the human eye.</span></h2>
                        <p>Interfaces shouldn't just be functional—they should be a <strong>kaleidoscope of awesomeness</strong>. I bring pixel-perfect designs to life with <strong>smooth animations</strong> and intuitive UX.</p>
                        <div class="hand-drawn-arrow" style="transform: rotate(180deg) scaleX(-1);">
                             <svg width="60" height="40" viewBox="0 0 60 40"><path d="M10,10 Q30,5 50,30 M50,30 L40,25 M50,30 L55,20" fill="none" stroke="#FFE227" stroke-width="2" /></svg>
                        </div>
                    </div>
                    <div class="polaroid-wrapper" style="--rotation: 3deg;">
                        <div class="tape-v2"></div>
                        <div class="polaroid-card">
                            <div class="card-inner">
                                <i class="fa-brands fa-react sticker react-sticker"></i>
                                <i class="fa-brands fa-vuejs sticker vue-sticker"></i>
                                <div class="skill-stack-list">
                                    <span>• Modern Vue (Composition API)</span>
                                    <span>• React & Next.js Ecosystem</span>
                                    <span>• CSS3 & Framer Motion</span>
                                    <span>• Responsive & Adaptive UI</span>
                                </div>
                            </div>
                            <div class="polaroid-footer">
                                <span class="caption">FRONTEND MAGIC ✨</span>
                            </div>
                        </div>
                    </div>
                </div>

                <!-- Slide 3: Tools -->
                <div class="skill-slide" :ref="el => setSlideRef(el, 2)">
                    <div class="slide-info">
                        <div class="badge">Workflow & Tools</div>
                        <h2>The secret <br><span>superpowers.</span></h2>
                        <p>A master is only as good as their tools. I leverage <strong>industrial-strength technologies</strong> to ensure my development workflow is <strong>lightning fast</strong> and error-free.</p>
                        <div class="hand-drawn-arrow" style="transform: rotate(20deg);">
                             <svg width="60" height="40" viewBox="0 0 60 40"><path d="M10,10 Q30,5 50,30 M50,30 L40,25 M50,30 L55,20" fill="none" stroke="#FFE227" stroke-width="2" /></svg>
                        </div>
                    </div>
                    <div class="polaroid-wrapper" style="--rotation: -1deg;">
                        <div class="tape-v2"></div>
                        <div class="polaroid-card">
                            <div class="card-inner">
                                <i class="fa-brands fa-git sticker git-sticker"></i>
                                <i class="fa-brands fa-figma sticker figma-sticker"></i>
                                <div class="skill-stack-list">
                                    <span>• Version Control & CI/CD</span>
                                    <span>• Figma-to-Code Mastery</span>
                                    <span>• SEO & Performance Metrics</span>
                                    <span>• Data Visualization (PowerBI)</span>
                                </div>
                            </div>
                            <div class="polaroid-footer">
                                <span class="caption">TO THE STARS!! 🚀</span>
                            </div>
                        </div>
                    </div>
                </div>
                 <div class="polaroid-card" style="--rotation: -1deg; height: 80%; background-color:whitesmoke; opacity: 0.80;">
                    <div class="card-inner">
                        <img class="Gifs" src="https://i.pinimg.com/originals/3f/3b/88/3f3b8883f6626fdfb36947316a42ed71.gif" alt=""  
                        style="opacity:0.90;">
                        </div>
                    <div class="polaroid-footer">
                        <span class="caption">The end!! 🚀</span>
                    </div>
                 </div>

            </div>
        </div>
    </div>
</template>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Gochi+Hand&family=Outfit:wght@400;700;800&family=Inter:wght@400;700&display=swap');

.sticky-parent {
    height: 400vh;
    background-color: white;
}

.sticky-child {
    position: sticky;
    top: 0;
    height: 100vh;
    width: 100%;
    overflow: hidden;
    display: flex;
    flex-direction: column;
    justify-content: center;
}

.section-title {
    position: absolute;
    top: 50px;
    left: 50%;
    transform: translateX(-50%);
    font-family: 'Outfit', sans-serif;
    font-size: 1.1rem;
    font-weight: 800;
    color: #121212;
    text-transform: uppercase;
    letter-spacing: 0.5rem;
    z-index: 20;
    background: white;
    padding: 8px 24px;
    border: 2px solid #121212;
    box-shadow: 4px 4px 0px #121212;
}

.grass-bg {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background-image: url('https://i.pinimg.com/originals/f8/6e/16/f86e16795f4bbbe5dfd213774d04fc4e.gif');
    background-size: cover;
    background-repeat: no-repeat;
    background-position: center;
    z-index: 1;
    pointer-events: none;
    opacity: 0.80; /* Adjusted for better card contrast */
}


.horizontal-track {
    display: flex;
    will-change: transform;
    padding-left: 5vw;
    margin-top: 12vh; /* Pushed cards down */
    position: relative;
    z-index: 10;
}

/* Arrow Animation */
.hand-drawn-arrow svg {
    overflow: visible;
}

.hand-drawn-arrow path {
    stroke-dasharray: 100;
    stroke-dashoffset: 100;
    animation: draw-arrow 2.5s ease-out infinite alternate;
}

@keyframes draw-arrow {
    0% { stroke-dashoffset: 100; opacity: 0; }
    50% { stroke-dashoffset: 0; opacity: 1; }
    100% { stroke-dashoffset: 0; opacity: 1; transform: scale(1.05) translate(2px, -2px); }
}

.skill-slide {
    flex-shrink: 0;
    width: 100vw;
    height: 80vh;
    display: flex;
    align-items: center;
    justify-content: center;
    gap: 6vw;
    padding-right: 10vw;
    opacity: 0;
    transform: translateY(20px);
    transition: all 1s cubic-bezier(0.4, 0, 0.2, 1);
}

.skill-slide.revealed {
    opacity: 1;
    transform: translateY(0);
}

.slide-info {
    max-width: 550px;
    text-align: left;
}

.badge {
    display: inline-block;
    padding: 6px 14px;
    background: transparent;
    border: 2.5px solid #121212;
    font-weight: 800;
    font-size: 0.8rem;
    margin-bottom: 2rem;
    text-transform: uppercase;
}

h2 {
    font-family: 'Outfit', sans-serif;
    font-size: 5rem;
    line-height: 0.95;
    font-weight: 800;
    color: #121212;
    margin-bottom: 1.8rem;
    letter-spacing: -0.02em;
}

h2 span {
    color: #121212;
    opacity: 0.4;
}

p {
    font-family: 'Inter', sans-serif;
    font-size: 1.45rem;
    line-height: 1.5;
    color: #121212;
    margin-bottom: 2rem;
    font-weight: 400;
}

p strong {
    font-weight: 700;
    border-bottom: 3px solid #FFE227;
}

/* Polaroid Card UI */
.polaroid-wrapper {
    position: relative;
    transform: rotate(var(--rotation));
    z-index: 5;
}

.polaroid-card {
    background: white;
    padding: 20px 20px 12px 20px;
    box-shadow: 0 30px 60px rgba(0,0,0,0.12);
    width: 380px; /* Smaller cards */
    border: 1px solid #eee;
}

.card-inner {
    background: #e9e9e9;
    height: 340px; /* Balanced height */
    position: relative;
    display: flex;
    align-items: center;
    justify-content: center;
    overflow: hidden;
}

.skill-stack-list {
    display: flex;
    flex-direction: column;
    gap: 15px;
    text-align: left;
    width: 80%;
    z-index: 5;
}

.skill-stack-list span {
    font-family: 'Outfit', sans-serif;
    font-size: 1.35rem; /* Slightly smaller for resized card */
    font-weight: 800;
    color: #121212;
}

/* Stickers */
.sticker {
    position: absolute;
    font-size: 6rem; /* Smaller stickers */
    opacity: 0.1;
    z-index: 1;
    pointer-events: none;
}

.node-sticker { top: -20px; right: -20px; transform: rotate(15deg); }
.py-sticker { bottom: -20px; left: -20px; transform: rotate(-10deg); }
.react-sticker { top: -20px; right: -20px; transform: rotate(20deg); }
.vue-sticker { bottom: -20px; left: -20px; transform: rotate(-5deg); }
.git-sticker { top: -20px; right: -20px; transform: rotate(12deg); }
.figma-sticker { bottom: -20px; left: -20px; transform: rotate(-20deg); }

.polaroid-footer {
    display: flex;
    flex-direction: column;
    align-items: flex-end; /* Align handwritten notes to bottom right */
    padding: 25px 10px 10px 0;
    position: relative;
}

.caption {
    font-family: 'Gochi Hand', cursive;
    font-size: 2.2rem; /* Scaled down */
    color: #121212;
    transform: rotate(-2deg);
    line-height: 1;
}

.star-rating {
    font-family: 'Gochi Hand', cursive;
    font-size: 1.8rem;
    color: #6366f1;
    margin-top: 5px;
}


.stamp {
    position: absolute;
    top: -40px;
    left: 0;
    border: 4px solid #ff4d4d;
    color: #ff4d4d;
    font-weight: 800;
    padding: 4px 12px;
    transform: rotate(-12deg);
    font-family: 'Outfit', sans-serif;
    font-size: 1.2rem;
    letter-spacing: 2px;
}

/* Tape */
.tape-v2 {
    position: absolute;
    top: -25px;
    left: 50%;
    transform: translateX(-50%) rotate(2deg);
    width: 160px;
    height: 55px;
    background: rgba(220, 210, 190, 0.7);
    backdrop-filter: blur(4px);
    z-index: 100;
    box-shadow: 0 4px 12px rgba(0,0,0,0.08);
}

</style>
