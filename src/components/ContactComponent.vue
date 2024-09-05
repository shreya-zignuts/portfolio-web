<template>
  <section class="contact" id="contact">
    <div class="contact-header">
      <h2 class="fade-in-up" ref="ContactText">Contact Me</h2>
      <h4 class="fade-in-up" style="animation-delay: 0.3s">Let's Work Together</h4>
      <p class="fade-in-up" style="animation-delay: 0.6s">
        I will help you in your next project. Contact me through the details below.
      </p>
    </div>
    <div
      class="contact-content fade-in-up"
      ref="ContactCards"
      style="animation-delay: 0.9s"
    >
      <div class="contact-cards">
        <div class="contact-card">
          <i class="bx bxs-map"></i>
          <a
            href="https://www.google.com/maps?q=Balasinor,+Mahisagar,+Gujarat"
            target="_blank"
            >Balasinor, Mahisagar, Gujarat</a
          >
        </div>
        <div class="contact-card">
          <i class="bx bxs-envelope"></i>
          <a href="mailto:shreyapatelegcs@gmail.com">shreyapatelegcs@gmail.com</a>
        </div>
        <div class="contact-card">
          <i class="bx bxs-phone"></i>
          <a href="tel:+917016802144">+91 7016802144</a>
        </div>
      </div>
      <a
        href="mailto:shreyapatelegcs@gmail.com"
        class="btn btn-chat fade-in-up"
        style="animation-delay: 1.2s"
      >
        Let's Chat
      </a>
    </div>
    <div
      class="contact-icons fade-in-up"
      ref="ContactIcons"
      style="animation-delay: 1.5s"
    >
      <a href="https://www.linkedin.com/in/shreya-patel-5a3355210" target="_blank"
        ><i class="bx bxl-linkedin"></i
      ></a>
      <a href="https://github.com/shreya-zignuts" target="_blank"
        ><i class="bx bxl-github"></i
      ></a>
      <a href="tel:+917016802144" title="WhatsApp"><i class="bx bxl-whatsapp"></i></a>
    </div>
  </section>
</template>

<script setup>
import { ref, onMounted } from "vue";
import { gsap } from "gsap";

const ContactText = ref(null);
const ContactCards = ref(null);
const ContactIcons = ref(null);

const animateOnScroll = (entries, observer) => {
  entries.forEach((entry) => {
    if (entry.isIntersecting) {
      // Animate header text
      gsap.fromTo(
        ContactText.value,
        { opacity: 0, y: -50, scale: 1.1 },
        { opacity: 1, y: 0, scale: 1, duration: 1.5, ease: "bounce.out" }
      );

      // Animate contact cards
      gsap.fromTo(
        ContactCards.value,
        { opacity: 0, scale: 0.9, y: 30 },
        {
          opacity: 1,
          scale: 1,
          y: 0,
          duration: 1,
          delay: 0.5,
          ease: "power2.out",
          stagger: 0.2,
        }
      );

      // Animate icons with zoom effect
      gsap.fromTo(
        ContactIcons.value,
        { opacity: 0, scale: 0.5 },
        { opacity: 1, scale: 1, duration: 1.2, delay: 1, ease: "back.out(1.7)" }
      );

      // Stop observing once the animation has been triggered
      observer.disconnect();
    }
  });
};

onMounted(() => {
  const observer = new IntersectionObserver(animateOnScroll, {
    root: null,
    rootMargin: "0px",
    threshold: 0.1,
  });

  observer.observe(ContactText.value);
  observer.observe(ContactCards.value);
  observer.observe(ContactIcons.value);
});
</script>

<style scoped>
/* Add your styling here */
</style>
