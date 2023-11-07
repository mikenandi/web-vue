<script setup lang="ts">
import { ref, onMounted } from "vue";

// reactive state
const count = ref(0);
const name = ref("michael");

// functions that mutate state and trigger updates
// function increment(): void {
//   count.value++;
// }

// lifecycle hooks
onMounted(() => {
  console.log(`The initial count is ${count.value}.`);
});

function greet(event: Event) {
  alert(`Hello ${name.value}!`);

  if (event) {
    alert();
  }
}
</script>

<template>
  <div class="about">
    <!-- <h2>
      This is an about page hellot this is amazing man and show
      scarry, ilove it
    </h2> -->
    <h3>{{ true ? "Yes" : "No" }}</h3>

    <button @click="count++">Count is: {{ count }}</button>
    <button @click="greet">greeting</button>
    but
  </div>
</template>

<style>
@media (min-width: 1024px) {
  .about {
    min-height: 100vh;
    display: flex;
    align-items: center;
  }
}
</style>
