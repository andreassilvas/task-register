<template>
  <footer>
    <p>Copyright &copy; 2024</p>
    <router-link to="/about" v-show="aboutPage" :style="{ color: '#1f67e7' }"
      >About</router-link
    >
  </footer>
</template>
<script>
export default {
  computed: {
    aboutPage() {
      if (this.$route.path === "/about") {
        return false;
      } else {
        return true;
      }
    },
  },
};
</script>
<style scope>
a {
  color: #333;
}
footer {
  margin-top: 30px;
  text-align: center;
}
</style>
