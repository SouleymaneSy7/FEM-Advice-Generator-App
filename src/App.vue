<template>
  <AdviceCard />
</template>

<script>
import AdviceCard from "./components/AdviceCard.vue";

export default {
  name: "App",
  components: {
    AdviceCard,
  },
};
</script>

<style lang="scss">
*,
*::before,
*::after {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
// Colors
$dark-blue: hsl(218, 23%, 16%);

// Fonts
$font-family: "Manrope", sans-serif;

body {
  width: 100%;
  height: 100vh;

  font-family: $font-family;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;

  display: flex;
  justify-content: center;
  align-items: center;

  background: $dark-blue;
  padding: 0 1.25rem;

  overflow: hidden;
}
</style>
