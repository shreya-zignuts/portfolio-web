<template>
  <section class="quote" id="quote">
    <div class="card">
      <blockquote>
        <p ref="quotation"></p>
        <footer>
          <p ref="source" class="source"></p>
        </footer>
      </blockquote>
      <button @click="generateQuote">Generate Quote</button>
    </div>
  </section>
</template>

<script setup>
import { ref, onMounted } from "vue";

const quotes = [
  {
    quote:
      "A man is his own easiest dupe, for what he wishes to be true he generally believes to be true",
    source: "Demosthenes",
  },
  {
    quote:
      "A lie can travel halfway around the world while the truth is putting on its shoes",
    source: "Mark Twain",
  },
  {
    quote:
      "Great minds discuss ideas; average minds discuss events; small minds discuss people",
    source: "Eleanor Roosevelt",
  },
  {
    quote: "If you have a garden and a library, you have everything you need",
    source: "Marcus Tullius Cicero",
  },
  {
    quote: "Everything in the universe is within you. Ask all from yourself",
    source: "Rumi",
  },
  {
    quote:
      "When I get a little money I buy books; and if any is left I buy food and clothes",
    source: "Desiderius Erasmus",
  },
];

const quotation = ref(null);
const source = ref(null);

function generateQuote() {
  const random = quotes[Math.floor(Math.random() * quotes.length)];
  if (quotation.value && source.value) {
    quotation.value.innerText = `“${random.quote}.”`;
    source.value.innerText = random.source;
  }
}

onMounted(() => {
  generateQuote();
});
</script>

<style scoped>
@import url("https://fonts.googleapis.com/css2?family=Quicksand:wght@400;600&display=swap");

button {
  font-family: "Quicksand", sans-serif;
  padding: 0.5rem 1rem;
  margin-top: 10px;
  font-size: 1rem;
  background: var(--main-color); /* Primary button color */
  border: none;
  border-radius: 25px; /* Rounded button corners */
  cursor: pointer;
  color: var(--text-color); /* Button text color */
  transition: background 0.3s ease;
}

button:hover {
  background: var(--second-color); /* Button hover color */
}
</style>
