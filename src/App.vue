<script setup lang="ts">
import './style.css';
import Navbar from './Navbar.vue';
import HeroSection from './components/HeroSection.vue';
import Marquee from './components/Marquee.vue';
import Stack from './components/Stack.vue';
import Expre from './components/Expre.vue';
import Project from './components/Project.vue';
import Socials from './components/Socials.vue';
import Footer from './components/Footer.vue';

</script>

<template>
  <Navbar />
  <main>
    <HeroSection />
    <Marquee />
    <Stack />
    <Expre />
    <Project />
    <Socials />
    <Footer />
  </main>
</template>

<style scoped>
body{
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  overflow-x: hidden;
  font-family: var(--font-body);
  background-color: #D4FDF7;
}
</style>
