<template>
  <button
    class="button"
    :style="{ background: bg, marginRight: mr, borderColor: bc, color: color }"
    @click="onClick()"
  >
    {{ text }}
  </button>
</template>
<script>
export default {
  name: "Button",
  props: { text: String, bg: String, mr: String, bc: String, color: String },
  methods: {
    onClick() {
      this.$emit("button-click");
    },
  },
};
</script>
