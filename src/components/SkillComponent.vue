<template>
    <section class="skills" id="skills">
      <div class="main-text">
        <h2 ref="SkillsText">My Skills</h2>
      </div>
  
      <div class="skills-content">
        <div class="box">
          <img src="../img/fe-devlop.jpg" alt="Front-end Development">
          <h3>Front-end Development</h3>
          <p>Front-end development involves crafting the visual and interactive aspects of a website or
            application. It’s about creating engaging user interfaces that provide a smooth and intuitive
            experience. By translating design concepts into functional code, front-end developers ensure that
            users have a pleasant and efficient interaction with digital products.</p>
        </div>
  
        <div class="box">
          <img src="../img/back-develop.png" alt="Back-end Development">
          <h3>Back-end Development</h3>
          <p>Back-end development focuses on the server side of web applications. It involves building and
            maintaining the technology that powers the front-end, such as databases, server logic, and APIs.
            Back-end developers work on server configurations, data management, and application performance,
            ensuring that the user-facing side operates smoothly and efficiently behind the scenes.</p>
        </div>
  
        <div class="box">
          <img src="../img/multi-task.png" alt="Dynamic Involvement">
          <h3>Dynamic Involvement</h3>
          <p>Dynamic involvement reflects an individual's active participation in a variety of activities, both
            technical and recreational. This skill encompasses engaging in diverse interests such as games,
            creative projects, and community initiatives. Those with dynamic involvement thrive in multiple
            contexts, leveraging their broad experiences to contribute effectively and adapt to various
            challenges. Their enthusiasm for a wide range of pursuits fosters creativity and a comprehensive
            approach to problem-solving.</p>
        </div>
      </div>
    </section>
  </template>
  
  <script setup>
  import { ref, onMounted } from 'vue';
  import { gsap } from 'gsap';
  
  const SkillsText = ref(null);
  
  const animateOnScroll = (entries) => {
    entries.forEach(entry => {
      if (entry.isIntersecting) {
        gsap.fromTo(SkillsText.value, 
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
  
    observer.observe(SkillsText.value);
  });
  </script>
  
  <!-- Add "scoped" attribute to limit CSS to this component only -->
  <style scoped>
    .main-text h2{
        font-size: 3rem;
        margin-bottom: 16px;
    }
  </style>
  