<template>
  <section class="achievement" id="achievement">
    <div class="main-text">
      <h2 ref="AchievementsText">My Achievements</h2>
      <h4>Some of My Major Achievements</h4>
    </div>

    <div class="portfolio-content">
      <div
        class="row"
        v-for="(achievement, index) in achievements"
        :key="index"
        ref="achievementRows"
      >
        <img
          :src="achievement.img"
          :alt="achievement.title"
          class="achievement-image"
          ref="achievementImages"
        />
        <div class="main-row">
          <div class="row-text">
            <h6>{{ achievement.title }}</h6>
          </div>
        </div>
        <h3>{{ achievement.description }}</h3>
      </div>
    </div>
  </section>
</template>

<script setup>
import { ref, onMounted } from "vue";
import { gsap } from "gsap";

const AchievementsText = ref(null);
const achievementRows = ref([]);
const achievementImages = ref([]);

const achievements = [
  {
    img: require("@/img/type.webp"),
    title: "Typing Wizard",
    description:
      "Participated in college competition typing competition, and reached the semifinals.",
  },
  {
    img: require("@/img/kbddi.avif"),
    title: "SGFI Kabaddi Player",
    description:
      "Represented my school as an SGFI (School Games Federation of India) Kabaddi player.",
  },
];

const animateOnScroll = (entries) => {
  entries.forEach((entry) => {
    if (entry.isIntersecting) {
      if (entry.target === AchievementsText.value) {
        gsap.fromTo(
          AchievementsText.value,
          { opacity: 0, y: -50 },
          { opacity: 1, y: 0, duration: 1.5, ease: "bounce.out" }
        );
      }
    }
  });
};

onMounted(() => {
  const observer = new IntersectionObserver(animateOnScroll, {
    root: null,
    rootMargin: "0px",
    threshold: 0.1,
  });

  if (AchievementsText.value) {
    observer.observe(AchievementsText.value);
  }

  achievementRows.value.forEach((row) => observer.observe(row));
  achievementImages.value.forEach((image) => observer.observe(image));
});
</script>

<style scoped>
@media (max-width: 830px) {
  .row {
    max-width: 480px;
  }
}
</style>
