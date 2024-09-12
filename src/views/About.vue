<template>
  <div>
    <p>{{ aboutText }}</p>
    <router-link to="/" :style="{ color: '#1f67e7' }">
      <i class="fa-solid fa-arrow-left"></i>
      {{ linkText }}</router-link
    >
  </div>
</template>
<script>
export default {
  data() {
    return {
      aboutText: "This app was implemented using Vue.js and Vue Router.",
      linkText: "Back to home page",
    };
  },
};
</script>
<style scoped>
p {
  margin: 30px 15px;
}
</style>
