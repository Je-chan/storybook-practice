<template>
  <button>
    <slot v-if="slots.default" />
    <span v-else>Button</span>
  </button>
</template>
<script setup>
// import { ref } from "vue";
import { useSlots } from "vue";
const props = defineProps({
  palette: String,
  size: String,
  w: String,
  h: String,
  c: String,
  ch: String,
  bc: String,
  bch: String,
  fs: String,
  fw: String,
  colored: String,
});

const slots = useSlots();

console.log(slots.default);

const stylePackage = {
  w: "100px",
  h: "35px",
  c: "#000",
  ch: "#fff",
  bc: "#fff",
  bch: "#000",
  fs: "18px",
  fw: "500",
};

const colorTheme = {
  blue: "#3386f7",
  lightBlue: "#7dcbf8",
  red: "#fa4b62",
  lightRed: "#f7929f",
  gray: "#8d97a1",
};

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

const { blue, lightBlue, red, lightRed, gray } = colorTheme;
const { xs, s, m, l, xl } = sizeTheme;

switch (props.palette) {
  case "blue":
    stylePackage.c = blue;
    stylePackage.bch = blue;
    break;
  case "lightBlue":
    stylePackage.c = lightBlue;
    stylePackage.bch = lightBlue;
    break;
  case "red":
    stylePackage.c = red;
    stylePackage.bch = red;
    break;
  case "lightRed":
    stylePackage.c = lightRed;
    stylePackage.bch = lightRed;
    break;
  case "gray":
    stylePackage.c = gray;
    stylePackage.bch = gray;
    break;
}

switch (props.size) {
  case "xs":
    stylePackage.w = xs.w;
    stylePackage.h = xs.h;
    break;
  case "s":
    stylePackage.w = s.w;
    stylePackage.h = s.h;
    break;
  case "m":
    stylePackage.w = m.w;
    stylePackage.h = m.h;
    break;
  case "l":
    stylePackage.w = l.w;
    stylePackage.h = l.h;
    break;
  case "xl":
    stylePackage.w = xl.w;
    stylePackage.h = xl.h;
    break;
}

const copiedProps = { ...props };

for (let key in copiedProps) {
  if (key === "palette") continue;
  if (props[key]) stylePackage[key] = copiedProps[key];
}

const { w, h, c, ch, bc, bch, fs, fw } = stylePackage;
</script>

<style lang="scss">
button {
  width: v-bind(w);
  height: v-bind(h);
  font-size: v-bind(fs);
  font-weight: v-bind(fw);
  border-radius: 5px;
  background: v-bind(bc);
  border: 2.5px solid v-bind(c);
  color: v-bind(c);
  transition: all 0.2s;
  &:hover {
    cursor: pointer;
    background-color: v-bind(bch);
    color: v-bind(ch);
  }
}
</style>
