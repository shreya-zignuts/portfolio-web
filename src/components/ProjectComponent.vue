<template>
  <section class="portfolio" id="portfolio">
    <div class="main-text">
      <h2 ref="ProjectsText">My Projects</h2>
      <h4>Some Of My Distinguished Works</h4>
    </div>

    <div class="portfolio-content">
      <div
        class="row"
        v-for="(project, index) in projects"
        :key="index"
        ref="projectRows"
      >
        <img
          :src="project.img"
          :alt="project.title"
          class="project-image"
          ref="projectImages"
        />
        <div class="main-row">
          <div class="row-text">
            <h6>{{ project.category }}</h6>
          </div>
        </div>
        <h3>{{ project.title }}</h3>
      </div>
    </div>
  </section>
</template>

<script setup>
import { ref, onMounted } from "vue";
import { gsap } from "gsap";

const ProjectsText = ref(null);
const projectRows = ref([]);
const projectImages = ref([]);

const projects = [
  {
    img: require("@/img/crm.png"),
    title: "CRM Project",
    category: "Web App Development",
  },
  {
    img: require("@/img/task.webp"),
    title: "Task Management",
    category: "Web App Development",
  },
  {
    img: require("@/img/exp.png"),
    title: "Expense Manager",
    category: "Web App Development",
  },
];

const animateOnScroll = (entries) => {
  entries.forEach((entry) => {
    if (entry.isIntersecting) {
      if (entry.target === ProjectsText.value) {
        gsap.fromTo(
          ProjectsText.value,
          { opacity: 0, y: -50 },
          { opacity: 1, y: 0, duration: 1.5, ease: "bounce.out" }
        );
      }

      if (projectRows.value.includes(entry.target)) {
        gsap.fromTo(
          entry.target,
          { opacity: 0, y: 50 },
          { opacity: 1, y: 0, duration: 1.5, stagger: 0.2, ease: "power3.out" }
        );
      }

      if (projectImages.value.includes(entry.target)) {
        gsap.fromTo(
          entry.target,
          { opacity: 0, scale: 0.9, rotation: -10 },
          {
            opacity: 1,
            scale: 1,
            rotation: 0,
            duration: 1.5,
            stagger: 0.2,
            ease: "power3.out",
          }
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

  if (ProjectsText.value) {
    observer.observe(ProjectsText.value);
  }

  projectRows.value.forEach((row) => observer.observe(row));
  projectImages.value.forEach((image) => observer.observe(image));
});
</script>

<style scoped>
.project-image {
  transition: transform 1.5s ease, opacity 1.5s ease;
  /* Optional: Add a box-shadow or border for a better effect */
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
}

.project-image.animate {
  transform: scale(1) rotate(0);
}
</style>
