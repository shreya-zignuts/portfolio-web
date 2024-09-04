<template>
  <section class="experience" id="experience">
    <div class="main-text">
      <h2 ref="ExperienceText">My Experience</h2>
    </div>
    <br>
    <div class="experience-content">
      <div class="box">
        <img src="../img/zignuts-logo.svg" alt="Zignuts Technolab Logo">
        <h3>Zignuts Technolab</h3>
        <h4>
          <span>Software Development Intern</span>
        </h4>
        <br>
        <p>
          • Completed an internship with a focus on PHP Laravel framework.<br>
          • Developed and implemented projects using PHP Laravel.<br>
          • Gained hands-on experience with Symfony and Vue.js during the internship.<br>
          • Created practice projects to strengthen skills in Symfony and Vue.js.
        </p>
      </div>
    </div>
  </section>
</template>

<script setup>
import { ref, onMounted } from 'vue';
import { gsap } from 'gsap';

const ExperienceText = ref(null);

const animateOnScroll = (entries) => {
  entries.forEach(entry => {
    if (entry.isIntersecting) {
      gsap.fromTo(ExperienceText.value, 
        { opacity: 0, y: -50, scale: 1.1 }, 
        { opacity: 1, y: 0, scale: 1, duration: 1.5, ease: 'bounce.out' }
      );
    }
  });
}

onMounted(() => {
  const observer = new IntersectionObserver(animateOnScroll, {
    root: null,
    rootMargin: '0px',
    threshold: 0.1
  });

  observer.observe(ExperienceText.value);
});
</script>

<style scoped>
</style>
