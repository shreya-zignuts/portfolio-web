<template>
    <section class="about" id="about">
      <div class="about-img-container">
        <div class="flowers-container" ref="flowersContainer">
          <div class="flower flower1"></div>
          <div class="flower flower2"></div>
          <div class="flower flower3"></div>
          <div class="flower flower4"></div> <!-- Added this line -->
        </div>
        <img ref="profileImg" src="../img/profile.jpg" alt="Profile Image">
      </div>
  
      <div class="about-text">
        <h2 ref="aboutTitle">About Me</h2>
        <h4 ref="nameTitle">Hi, My name is Shreya Patel !!</h4><br/>
        <p ref="introText">I recently completed my B.Tech degree in Information Technology at GEC, Modasa. With a strong passion for
          problem-solving and a drive for exploring innovative and dynamic ideas, I’m excited to apply the skills
          and knowledge I’ve gained to real-world challenges.</p>
        <p ref="skillsText">I am a Web Developer with expertise in both front-end and back-end technologies. I excel at creating
          efficient, maintainable code and developing robust server-side solutions, as well as delivering
          high-quality, user-friendly designs.</p>
        <div class="about-gri">
          <div class="about-in" ref="skill1">
            <h5>1. Problem Solving</h5>
          </div>
          <div class="about-in" ref="skill2">
            <h5>2. Web Development</h5>
          </div>
        </div>
        <a href="#contact" class="btn">Contact Me</a>
      </div>
    </section>
  </template>

<script setup>
import { ref, onMounted } from 'vue';
import gsap from 'gsap';

const profileImg = ref(null);
const flowersContainer = ref(null);
const aboutTitle = ref(null);
const nameTitle = ref(null);
const introText = ref(null);
const skillsText = ref(null);
const skill1 = ref(null);
const skill2 = ref(null);

const animateOnScroll = (entries) => {
  entries.forEach(entry => {
    if (entry.isIntersecting) {
      gsap.from(profileImg.value, {
        opacity: 0,
        scale: 1.2,
        duration: 2,
        ease: 'power2.out',
        delay: 0.5
      });

      gsap.from(flowersContainer.value.children, {
        opacity: 0,
        scale: 0.5,
        duration: 1.5,
        ease: 'elastic.out(1, 0.3)',
        stagger: 0.3,
        delay: 0.5
      });

      gsap.from(aboutTitle.value, {
        opacity: 0,
        y: -50,
        scale: 0.9,
        duration: 1,
        ease: 'bounce.out',
        delay: 1
      });

      gsap.from(nameTitle.value, {
        opacity: 0,
        y: 50,
        scale: 0.9,
        duration: 1,
        ease: 'bounce.out',
        delay: 1.5
      });

      gsap.from([introText.value, skillsText.value], {
        opacity: 0,
        y: 30,
        duration: 1.5,
        delay: 2,
        stagger: 0.3,
        ease: 'power3.out'
      });
      
      gsap.from([skill1.value], {
        opacity: 0,
        y: 30,
        duration: 1.5,
        delay: 2,
        stagger: 0.3,
        ease: 'power3.out'
      });
      
      gsap.from([skill2.value], {
        opacity: 0,
        y: 30,
        duration: 1.5,
        delay: 2,
        stagger: 0.3,
        ease: 'power6.out'
      });
    }
  });
};

onMounted(() => {
  const observer = new IntersectionObserver(animateOnScroll, {
    root: null,
    rootMargin: '0px',
    threshold: 0.1
  });

  observer.observe(document.querySelector('.about'));
});
</script>

<style scoped>

.about-img-container {
  position: relative;
  width: 100%;
  max-width: 460px; /* Set max width as needed */
  height: 100%; /* Adjust height as needed */
  display: flex;
  justify-content: center;
  align-items: center;
  margin: 0 auto; /* Center horizontally */
  overflow: hidden;
}

.flowers-container {
  position: absolute;
  width: 100%;
  height: 100%;
  top: 0;
  left: 0;
  display: flex;
  justify-content: center;
  align-items: center;
  pointer-events: none;
}

.flower {
  position: absolute;
  background-size: cover;
  background-repeat: no-repeat;
  width: 60px; /* Adjust size as needed */
  height: 60px; /* Adjust size as needed */
  z-index: 0;
}

.flower1 {
  background-image: url('https://cdn.pixabay.com/photo/2016/01/20/17/19/flower-1151970_1280.png'); /* Replace with your flower image */
  top: 0;
  left: 0;
  transform: translate(-50%, -50%); /* Center the flower */
}

.flower2 {
  background-image: url('https://cdn.pixabay.com/photo/2016/01/20/17/19/flower-1151970_1280.png'); /* Replace with your flower image */
  top: 0;
  right: 0;
  transform: translate(50%, -50%); /* Center the flower */
}

.flower3 {
  background-image: url('https://cdn.pixabay.com/photo/2016/01/20/17/19/flower-1151970_1280.png'); /* Replace with your flower image */
  bottom: 0;
  left: 0;
  transform: translate(-50%, 50%); /* Center the flower */
}

.flower4 {
  background-image: url('https://cdn.pixabay.com/photo/2016/01/20/17/19/flower-1151970_1280.png'); /* Replace with your flower image */
  bottom: 0;
  right: 0;
  transform: translate(50%, 50%); /* Center the flower */
}

.about-img-container img {
  width: 116%;
  height: 100%;/* Ensures image covers the container's height */
  object-fit: cover; /* Ensures image covers the container without distortion */
  display: block;
  position: relative;
  z-index: 1;
}

.about-text {
  padding: 2rem;
  position: relative;
  z-index: 2;
}

.about-gri {
  display: flex;
  flex-wrap: wrap;
  gap: 1rem;
}

.about-in {
  flex: 1;
  /* Add your styles here */
}

</style>