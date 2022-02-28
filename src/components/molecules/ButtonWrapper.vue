<template>
  <div class="flex-wrap">
    <CustomizedButton size="xl">안녕</CustomizedButton>
    <CustomizedButton size="xl"></CustomizedButton>
  </div>
</template>

<script setup>
// import { ref } from "vue";
import CustomizedButton from "../atoms/CustomizedButton.vue";

const sizeTheme = {
  xs: {
    w: "40px",
    h: "30px",
  },
  s: {
    w: "60px",
    h: "35px",
  },
  m: {
    w: "100px",
    h: "35px",
  },
  l: {
    w: "300px",
    h: "50px",
  },
  xl: {
    w: "500px",
    h: "100px",
  },
};

const wrapperHeight = `${(Number(sizeTheme.xl.h.slice(0, -2)) + 20) * 2}px`;
</script>

<style scoped lang="scss">
.flex-wrap {
  display: flex;
  height: v-bind(wrapperHeight);
  flex-direction: column;
  justify-content: space-around;
}
</style>
