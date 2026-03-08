<script setup lang="ts">
</script>

<template>
    <section class="hero">
        <!-- Decorative Illustrations -->
        <div class="hero-vectors">
            <img src="https://shardeum.instawp.xyz/wp-content/themes/shardeum/img/home/hero-shape4@2x.png" class="vector v1" alt="">
            <img src="https://shardeum.instawp.xyz/wp-content/themes/shardeum/img/home/hero-shape5@2x.png" class="vector v2" alt="">
            <img src="https://shardeum.instawp.xyz/wp-content/themes/shardeum/img/home/hero-shape5@2x.png" class="vector v3" alt="">
            <img src="https://shardeum.instawp.xyz/wp-content/themes/shardeum/img/home/hero-shape5@2x.png" class="vector v4" alt="">
            <img  src="https://shardeum.instawp.xyz/wp-content/themes/shardeum/img/home/hero-shape4@2x.png" class="vector v5" alt="">
        </div>

        <div class="hero-left">
            <div class="content">
                <h1>Building Premium Digital Experiences</h1>
                <p>Kesari Brahmarishendra: UI/UX Designer & Web Developer crafting high-performance interfaces and scalable solutions.</p>
                <div class="cta-container">
                    <a href="mailto:brahmarishi868@gmail.com" class="try-button" style="text-decoration: none;">Connect Me <i class="fa-solid fa-arrow-right"></i></a>
                    <div class="mainShadow"></div>
                    <div class="button-shadow"></div>
                </div>
                <div class="direct-contact">
                    <i class="fa-solid fa-phone"></i> +91 868XXXXXXX <!-- I'll use a placeholder or generic format if unspecified, but user said "on hero number" -->
                    <!-- Re-reading: "on hero number" might mean "my number on hero" -->
                </div>
            </div>
        </div>
        <div class="hero-right">
            <div class="grid-overlay" :style="{ backgroundImage: 'url(https://i.pinimg.com/originals/f1/4a/5e/f14a5e0b51ae8bb0639d2800a6129a66.gif)' }"></div>
        </div>
    </section>
</template>

<style scoped>
.hero {
    display: flex;
    min-height: 80vh; /* Reduced from 100vh */
    padding-top: 90px;
    max-height: 800px;
}

.hero-left {
    flex: 1;
    background-color: #e0d7ff; /* Lavender */
    display: flex;
    align-items: center;
    justify-content: center;
    padding: 2rem 4rem; /* Reduced vertical padding */
}

.hero-left .content {
    max-width: 500px;
}

h1 {
    font-size: 4rem;
    line-height: 1.1;
    font-weight: 800;
    margin-bottom: 2rem;
    color: #121212;
}

p {
    font-size: 1.25rem;
    color: #121212;
    margin-bottom: 2rem; /* Adjusted */
    max-width: 400px;
}

.direct-contact {
    margin-top: 1.5rem;
    font-size: 1rem;
    font-weight: 700;
    color: #0d0d21;
    display: flex;
    align-items: center;
    gap: 10px;
    opacity: 0.8;
}

.cta-container {
    position: relative;
    display: inline-block;
}

.try-button {
    background: #0d0d21;
    color: white;
    padding: 1.2rem 2.5rem;
    border-radius: 1px;
    font-size: 1.1rem;
    font-weight: 700;
    display: flex;
    align-items: center;
    gap: 12px;
    position: relative;
    z-index: 2;
    transition: transform 0.2s ease;
}

.button-shadow {
    position: absolute;
    top: 6px;
    left: 6px;
    width: 100%;
    height: 100%;
    background: rgba(0, 0, 55, 0.2);
    border: 1px solid #0d0d21;
    border-radius: 1px;
    z-index: 1;
}

.mainShadow{
    position: absolute;
    top: -8px;
    left: -8px;
    width: 100%;
    height: 100%;
    background: rgba(0, 0, 55, 0.2);
    border: 1px solid #0d0d21;
    border-radius: 1px;
    z-index: 1;
}   

.try-button:hover {
    transform: translatex(6px);
    background-color: rgb(3, 3, 75);
}

.hero-right {
    flex: 1.2;
    background-color: #ffdb58; /* Yellow */
    position: relative;
    display: flex;
    align-items: flex-end;
    justify-content: center;
    overflow: hidden;
}

.grid-overlay {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background-size: cover;
    background-position: center;
     /* Subtle overlay */
    z-index: 1;
}

/* Floating Illustrations Stylings */
.hero-vectors {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    pointer-events: none;
    z-index: 1;
    overflow: hidden;
}

.vector {
    position: absolute;
    opacity: 0.30;
    animation: float 8s ease-in-out infinite;
}

.v1 { top: 15%; left: 5%; width: 100px; height: 100px; opacity: 0.90; animation-delay: 0s; }
.v2 { top: 25%; left: 40%; width: 60px; animation-delay: -2s; transform: rotate(15deg); opacity: 0.90; }
.v3 { top: 60%; left: 15%; width: 100px; animation-delay: -4s; transform: rotate(-10deg); opacity: 0.30; }
.v4 { top: 10%; right: 10%; width: 70px; animation-delay: -1s; opacity: 0.30; }
.v5 { top: 70%; right: 5%; width: 120px; animation-delay: -3s; opacity: 0.30; }

@keyframes float {
    0%, 100% { transform: translateY(0) rotate(0); }
    33% { transform: translateY(-15px) rotate(5deg); }
    66% { transform: translateY(10px) rotate(-5deg); }
}

@media screen and (max-width: 1200px) {
    .v2, .v4 { display: none; } /* Reduce clutter on mobile */
    .v1 { top: 5%; left: 5%; width: 50px; }
    .v3 { bottom: 10%; left: 10%; width: 60px; }
    .v5 { bottom: 5%; right: 5%; width: 80px; }
}

@media screen and (max-width: 1200px) {
    h1 { font-size: 3rem; }
    .hero { 
        flex-direction: column; /* Text first, GIF below */
        min-height: auto;
        max-height: none;
    }
    .hero-left, .hero-right { 
        flex: none; 
        width: 100%; 
        padding: 6rem 2rem; /* Consistent padding */
    }
    .hero-right {
        min-height: 250px; /* More space for the GIF background */
    }
}

@media screen and (max-width: 768px) {
    h1 { font-size: 2.5rem; }
    .hero-left { padding: 4rem 1.5rem; }
    .hero-right {
        min-height: 200px;
    }
}
</style>
