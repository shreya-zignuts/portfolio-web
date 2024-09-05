<!-- <template>
  <section class="home" id="home">
    <div class="home-text">
      <h4>Hello</h4>
      <h1>I'm <span>Shreya</span></h1>
      <h3 ref="textElement">Software Developer</h3>
      <a
        href="https://drive.google.com/file/d/1e2daq3JteAb5_oZ8JwHHqeNlumubOHjM/view?usp=drive_link"
        class="btn"
        target="_blank"
      >
        Download Resume
      </a>
    </div>
  </section>
</template>

<script setup>
import { ref, onMounted } from 'vue';
import { gsap } from "gsap";
import { TextPlugin } from "gsap/TextPlugin";

gsap.registerPlugin(TextPlugin);

const textElement = ref(null);

onMounted(() => {
  const textContent = "Software Developer";
  const splitText = textContent.split(""); // Split text into individual letters
  textElement.value.innerHTML = splitText.map(letter => `<span>${letter}</span>`).join("");

  gsap.fromTo(
    textElement.value.querySelectorAll("span"),
    { opacity: 0, y: 50 }, // Start from below with 0 opacity
    {
      opacity: 1,
      y: 0,
      duration: 1,
      ease: "power1.inOut",  // Dramatic easing
      stagger: 0.1,        // Delay between each letter animation
      repeat: -1,
      repeatDelay: 2,
      yoyo: true,
      delay: 2,
    }
  );
});
</script> 


  <style scoped>
  </style> -->

<template>
  <section class="home" id="home">
    <div class="home-text">
      <h4>Hello</h4>
      <h1>I'm <span class="animated-text">Shreya</span></h1>
      <h3 ref="textElement">Software Developer</h3>
      <a
        href="https://drive.google.com/file/d/1e2daq3JteAb5_oZ8JwHHqeNlumubOHjM/view?usp=drive_link"
        class="btn"
        target="_blank"
      >
        Download Resume
      </a>
    </div>
  </section>
</template>

<script setup>
import { ref, onMounted } from "vue";
import { gsap } from "gsap";
import { TextPlugin } from "gsap/TextPlugin";

gsap.registerPlugin(TextPlugin);

const textElement = ref(null);

onMounted(() => {
  const textContent = "Software Developer";
  const splitText = textContent.split(""); // Split text into individual letters
  textElement.value.innerHTML = splitText
    .map((letter) => `<span>${letter}</span>`)
    .join("");

  gsap.fromTo(
    textElement.value.querySelectorAll("span"),
    { opacity: 0, y: 50 }, // Start from below with 0 opacity
    {
      opacity: 1,
      y: 0,
      duration: 1,
      ease: "power1.inOut", // Dramatic easing
      stagger: 0.1, // Delay between each letter animation
      repeat: -1,
      repeatDelay: 2,
      yoyo: true,
      delay: 2,
    }
  );

  // Flower animation for the "Shreya" text
  gsap.to(".animated-text", {
    scale: 1.5,
    rotation: 360,
    duration: 4,
    repeat: -1,
    repeatDelay: 3,
    ease: "elastic.out(1, 0.3)",
    yoyo: true,
    transformOrigin: "center center",
  });
});
</script>

<style scoped>
.animated-text {
  display: inline-block;
  font-weight: bold;
  color: #7729a5; /* Adjust color as needed */
}
</style>
