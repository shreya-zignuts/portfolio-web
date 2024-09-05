<template>
  <header>
    <h2 class="logo">Portfo<span>lio</span></h2>
    <ul class="navbar">
      <li><a href="#home">Home</a></li>
      <li><a href="#about">About Me</a></li>
      <li><a href="#languages">Languages</a></li>
      <li><a href="#experience">Experience</a></li>
      <li><a href="#skills">Skills</a></li>
      <li><a href="#portfolio">Projects</a></li>
      <li><a href="#achievement">Achievements</a></li>
      <li class="contact-me"><a href="#contact">Contact</a></li>
    </ul>
    <div id="menu-icon" class="bx bx-menu"></div>
  </header>
</template>

<script setup>
import { onMounted } from 'vue';

onMounted(() => {
  const menu = document.querySelector('#menu-icon');
  const navbar = document.querySelector('.navbar');

  menu.onclick = () => {
    menu.classList.toggle('bx-x');
    navbar.classList.toggle('active');
  };

  window.onscroll = () => {
    menu.classList.remove('bx-x');
    navbar.classList.remove('active');
  };
});
</script>

<style scoped>
</style>
