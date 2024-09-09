<template>
  <section class="languages" id="languages">
    <div class="inner">
      <div class="Tech_header">
        <h1 ref="LanguageText">Languages</h1>
      </div>
      <div class="carousel-container">
        <div class="carousel">
          <div class="Tcontainer">
            <div class="skill-box" v-for="(skill, index) in skills" :key="index">
              <div class="skill-title">
                <div class="tech_img">
                  <img :src="skill.img" :alt="skill.name" class="skill-icon" />
                </div>
                <h3>{{ skill.name }}</h3>
              </div>
              <div class="skill-progress">
                <div class="progress-bar" :style="{ width: skill.level + '%' }">
                  {{ skill.level }}%
                </div>
              </div>
            </div>
            <div class="skill-box" v-for="(skill, index) in skills" :key="'dup-' + index">
              <div class="skill-title">
                <div class="tech_img">
                  <img :src="skill.img" :alt="skill.name" class="skill-icon" />
                </div>
                <h3>{{ skill.name }}</h3>
              </div>
              <div class="skill-progress">
                <div class="progress-bar" :style="{ width: skill.level + '%' }">
                  {{ skill.level }}%
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import { ref, onMounted } from "vue";
import { gsap } from "gsap";

const LanguageText = ref(null);
const skills = [
  { name: "C++", img: require("@/img/C++.png"), level: 70 },
  { name: "HTML", img: require("@/img/html-5.png"), level: 95 },
  { name: "CSS", img: require("@/img/css-3.png"), level: 70 },
  { name: "JavaScript", img: require("@/img/js.png"), level: 70 },
  { name: "JQuery", img: require("@/img/social.png"), level: 60 },
  { name: "PHP", img: require("@/img/php.png"), level: 85 },
  { name: "Laravel", img: require("@/img/icons8-laravel-64.png"), level: 90 },
  { name: "Symfony", img: require("@/img/symfony-seeklogo.svg"), level: 70 },
  { name: "Vue JS", img: require("@/img/icons8-vue-js-96.png"), level: 40 },
];

const animateOnScroll = (entries) => {
  entries.forEach((entry) => {
    if (entry.isIntersecting) {
      gsap.fromTo(
        LanguageText.value,
        { opacity: 0, y: -50, scale: 1.2 },
        { opacity: 1, y: 0, scale: 1, duration: 1.5, ease: "bounce.out" }
      );
    }
  });
};

onMounted(() => {
  const observer = new IntersectionObserver(animateOnScroll, {
    root: null,
    rootMargin: "0px",
    threshold: 0.1,
  });

  observer.observe(document.querySelector(".inner"));

  const container = document.querySelector(".Tcontainer");
  const containerWidth = container.scrollWidth / 2;

  gsap.fromTo(
    container,
    { x: 0 },
    {
      x: `-${containerWidth}px`,
      duration: 20,
      ease: "none",
      repeat: -1,
      modifiers: {
        x: gsap.utils.unitize((x) => parseFloat(x) % containerWidth), 
      },
    }
  );
});
</script>

<style scoped>
.carousel-container {
  overflow: hidden;
  position: relative; /* Ensure the container handles overflow correctly */
}

.Tcontainer {
  display: flex;
  width: calc(100% * 2); /* Double the width for the duplicated content */
  will-change: transform;
}

h1 {
  font-size: 3.5rem;
}

.skill-box {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  height: 100%;
  width: 100%;
  box-shadow: 0px 0px 10px rgba(0, 0, 0, 0.1);
  border-radius: 10px;
}

.skill-progress {
  width: 100%;
  border-radius: 10px;
  overflow: hidden;
}

.progress-bar {
  height: 20px;
  color: white;
  text-align: center;
}
</style>
