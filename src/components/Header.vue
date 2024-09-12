<template>
  <header>
    <h1>
      <img class="brandLogo" :src="brandLogo" alt="brand logo" />
      {{ title }}
    </h1>
    <Button
      v-show="homePage"
      :text="toggleButtonState ? 'Close' : 'Add Task'"
      :bg="toggleButtonState ? '#fff' : ''"
      :bc="toggleButtonState ? '#fff' : ''"
      :color="toggleButtonState ? '#BE4144' : ''"
      @button-click="$emit('toggle-add-task')"
    />
  </header>
</template>
<script>
import Button from "./Button.vue";
import brandLogo from "../assets/brandLogo.png";
export default {
  name: "Header",
  emits: ["toggle-add-task"],
  props: { title: String, toggleButtonState: Boolean },
  components: {
    Button,
  },
  data() {
    return {
      brandLogo: brandLogo,
    };
  },
  computed: {
    homePage() {
      if (this.$route.path === "/") {
        return true;
      } else {
        return false;
      }
    },
  },
};
</script>
<style scoped>
header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 20px;
}
.brandLogo {
  height: 35px;
}
</style>
