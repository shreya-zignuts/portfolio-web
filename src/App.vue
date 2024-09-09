<template>
  <!-- <img alt="Vue logo" src="./assets/logo.png"> -->
  <HeaderComponent/>
  <HomeComponent/>
  <AboutMe/>
  <LanguageComponent/>
  <QuoteGenerate/>
  <ExperienceComponent/>
  <SkillComponent/>
  <ProjectComponent/>
  <AchievementComponent/>
  <ContactComponent/>
</template>

<script setup>
import 'boxicons/css/boxicons.min.css';
import { onMounted } from 'vue';
import ScrollReveal from 'scrollreveal';

import HeaderComponent from './components/HeaderComponent.vue';
import AboutMe from './components/AboutMe.vue';
import HomeComponent from './components/HomeComponent.vue';
import LanguageComponent from './components/LanguageComponent.vue';
import QuoteGenerate from './components/QuoteGenerate.vue';
import ExperienceComponent from './components/ExperienceComponent.vue';
import SkillComponent from './components/SkillComponent.vue';
import ProjectComponent from './components/ProjectComponent.vue';
import AchievementComponent from './components/AchievementComponent.vue';
import ContactComponent from './components/ContactComponent.vue';

onMounted(() => {
  const header = document.querySelector("header");

  window.addEventListener("scroll", function () {
    header.classList.toggle("sticky", window.scrollY > 0);
  });

  const sr = ScrollReveal({
    distance: '25px',
    duration: 250,
    reset: true
  });

  sr.reveal('.home-text', { delay: 190, origin: 'bottom' });
  sr.reveal('.about, .services, .portfolio, .contact', { delay: 200, origin: 'bottom' });
});
</script>

<style>
</style>
