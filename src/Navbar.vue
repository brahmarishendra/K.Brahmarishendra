<script setup lang="ts">
import { ref } from 'vue';

const isOpen = ref(false);
const arrowAnimation = ref(false);

const toggleMenu = () => {
    isOpen.value = !isOpen.value;
}

const handleArrowAnimation = () => {
    arrowAnimation.value = !arrowAnimation.value;
}

</script>

<template>
    <nav class="navbar">
        <div class="nav-container">
            <div class="logo">
                <a href="">
                    <img src="@/assets/My Logo.jpg" alt="My Logo">
                    <span>K.Brahmarishendra</span>
                </a>
            </div>
            
            <!-- Desktop Links -->
            <ul class="nav-links desktop-only">
                <li class="nav-item">
                    <a href="#experience">Experience</a>
                    <div class="nav-shadow"></div>
                </li>
                <li class="nav-item">
                    <a href="#projects">Projects</a>
                    <div class="nav-shadow"></div>
                </li>
                <li class="nav-item">
                    <a href="#socials">Socials</a>
                    <div class="nav-shadow"></div>
                </li>
            </ul>

            <div class="nav-actions desktop-only">
                <a href="https://github.com/brahmarishendra" class="login-link">
                    <img src="https://img.icons8.com/?size=100&id=106562&format=png&color=000000" alt="" class="git">
                    My Github
                </a>
                <div class="cta-wrapper">
                    <a href="mailto:brahmarishi868@gmail.com" class="start-button" @mouseenter="handleArrowAnimation" @mouseleave="handleArrowAnimation">
                        Connect me <i :class="arrowAnimation ? 'fa-solid fa-arrow-right' : 'fa-solid fa-arrow-right'"> </i>
                    </a>
                    <div class="button-shadow-nav"></div>
                </div>
            </div>

            <div class="hamburger" @click="toggleMenu">
                <i class="fa-solid fa-bars"></i>
            </div>
        </div>

        <!-- Full-screen Mobile Menu Overlay -->
        <div class="mobile-overlay" :class="{ 'active': isOpen }">
            <div class="mobile-header">
                <div class="logo">
                    <a href="#" @click="toggleMenu">
                        <img src="@/assets/My Logo.jpg" alt="My Logo" class="mobile-logo-img">
                        <span>K.Brahmarishendra</span>
                    </a>
                </div>
                <div class="close-menu" @click="toggleMenu">
                    <i class="fa-solid fa-xmark"></i>
                </div>
            </div>

            <!-- CTA SECTION MOVED TO TOP -->
            <div class="mobile-cta-top">
                <a href="mailto:brahmarishi868@gmail.com" class="head-btn mobile-start-btn" style="text-decoration: none;" @click="toggleMenu">
                    Connect me <i class="fa-solid fa-arrow-right"></i>
                </a>
            </div>

            <nav class="mobile-nav">
                <ul class="mobile-links">
                    <li><a href="#experience" @click="toggleMenu">Experience <i class="fa-solid fa-arrow-right-long"></i></a></li>
                    <li><a href="#projects" @click="toggleMenu">Projects <i class="fa-solid fa-arrow-right-long"></i></a></li>
                    <li><a href="#socials" @click="toggleMenu">Socials <i class="fa-solid fa-arrow-right-long"></i></a></li>
                    <li><a href="https://github.com/brahmarishendra" @click="toggleMenu">My Github <i class="fa-solid fa-arrow-right-long"></i></a></li>
                </ul>
            </nav>
        </div>
    </nav>
</template>

<style scoped>
.navbar {
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 90px;
    background: white;
    display: flex;
    justify-content: center;
    align-items: center;
    z-index: 1000;
    border-bottom: 1px solid #333333;
}

.nav-container {
    width: 90%;
    max-width: 1300px;
    display: flex;
    justify-content: flex-start;
    align-items: center;
    gap: 2rem;
}

.logo {
    margin-right: auto;
}

.logo a {
    display: flex;
    align-items: center;
    gap: 12px;
    font-size: 1.4rem;
    font-weight: 800;
    color: #121212;
    text-decoration: none;
    font-family: var(--font-heading);
}

.logo img, .mobile-logo-img {
    width: 40px;
    height: 40px;
    border-radius: 50%;
    object-fit: cover;
    border: 1.5px solid #121212;
}

.nav-links {
    display: flex;
    list-style: none;
    gap: 1.5rem;
    align-items: center;
}

.nav-item {
    position: relative;
    list-style: none;
}

.nav-links li a {
    text-decoration: none;
    color: #121212;
    font-weight: 600;
    font-size: 1rem;
    padding: 0.6rem 1.4rem;
    border: 1.5px solid #121212;
    border-radius: 50px; /* Pill shape */
    background: rgb(254, 255, 254);
    transition: all 0.2s ease;
    position: relative;
    z-index: 2;
    display: block;
}

.nav-shadow {
    position: absolute;
    top: 4px;
    left: 4px;
    width: 100%;
    height: 100%;
    background: rgb(249, 247, 187); /* Light yellow shadow */
    border: 1.5px solid #121212;
    border-radius: 50px;
    z-index: 1;
    transition: all 0.2s ease;
}

.nav-item:hover a {
    transform: translate(-1px, -1px);
    background-color: #f7f7d7;
}

.nav-item:hover .nav-shadow {
    transform: translate(1px, 1px);
}

.nav-actions {
    display: flex;
    align-items: center;
    gap: 1.5rem;
}

.login-link {
    color: #121212;
    font-weight: 600;
    text-decoration: none;
    padding: 0.6rem 1.4rem;
    transition: all 0.2s ease;
    display: flex;
    align-items: center;
    gap: 8px;
}

.login-link .git {
    width: 20px;
    height: 20px;
    transition: transform 0.3s ease;
}

.login-link:hover .git {
    transform: rotate(15deg) scale(1.1);
}

.login-link:hover {
    background-color: #f5f5f5;
    border-radius: 50px;
}

.cta-wrapper {
    position: relative;
}

.start-button {
    background: #0d0d21;
    color: white;
    padding: 0.7rem 1.6rem;
    border-radius: 50px; /* Consistent Pill shape */
    font-weight: 600;
    display: flex;
    align-items: center;
    gap: 10px;
    text-decoration: none;
    border: 1.5px solid #0d0d21;
    transition: all 0.2s ease;
    position: relative;
    z-index: 2;
}

.button-shadow-nav {
    position: absolute;
    top: 4px;
    left: 4px;
    width: 100%;
    height: 100%;
    background: rgba(13, 13, 33, 0.2);
    border: 1.5px solid #0d0d21;
    border-radius: 50px;
    z-index: 1;
    transition: all 0.2s ease;
}

.cta-wrapper:hover .start-button {
    transform: translate(-1px, -1px);
}

.cta-wrapper:hover .button-shadow-nav {
    transform: translate(1px, 1px);
    background: rgba(13, 13, 33, 0.3);
}

/* Mobile Overlay Styles */
.mobile-overlay {
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 100vh;
    background: white;
    z-index: 2000;
    display: flex;
    flex-direction: column;
    padding: 2rem;
    transform: translateX(100%);
    transition: transform 0.4s cubic-bezier(0.4, 0, 0.2, 1);
    background-color: #fcfcfc;
}

.mobile-overlay.active {
    transform: translateX(0);
}

.mobile-header {
    display: flex;
    justify-content: space-between;
    align-items: center;
    margin-bottom: 3rem;
}

.close-menu {
    font-size: 2.5rem;
    cursor: pointer;
    color: #333;
}

.mobile-nav {
    flex: 1;
}

.mobile-links {
    list-style: none;
    display: flex;
    flex-direction: column;
    gap: 1.5rem;
}

.mobile-links li a {
    font-size: 1.8rem;
    font-weight: 700;
    color: #2c2c2c;
    text-decoration: none;
    display: flex;
    justify-content: space-between;
    align-items: center;
}

.mobile-links li a i {
    font-size: 1.2rem;
    color: #666;
}

.mobile-footer {
    margin-top: auto;
    display: flex;
    flex-direction: column;
    gap: 1.5rem;
}

.search-section {
    position: relative;
    border-top: 2px solid #000;
    padding-top: 1.5rem;
    display: flex;
    align-items: center;
    gap: 1rem;
}

.search-section i {
    font-size: 1.2rem;
    color: #333;
}

.search-section input {
    width: 100%;
    border: none;
    background: transparent;
    font-size: 1.2rem;
    font-weight: 600;
    outline: none;
    color: #333;
}

.mobile-cta-top {
    margin-bottom: 2rem;
    padding: 0 0.5rem;
}

.cta-section {
    padding-bottom: 1rem;
}

.head-btn {
    width: 100%;
    background-color: #ffb800; /* Yellow */
    color: #000;
    border: none;
    padding: 1.2rem;
    font-size: 1.2rem;
    font-weight: 700;
    border-radius: 4px;
    display: flex;
    justify-content: space-between;
    align-items: center;
    cursor: pointer;
}

.hamburger {
    display: none;
    cursor: pointer;
    font-size: 1.5rem;
    color: #333;
}

@media screen and (max-width: 992px) {
    .desktop-only {
        display: none;
    }

    .hamburger {
        display: block;
    }
}
</style>
