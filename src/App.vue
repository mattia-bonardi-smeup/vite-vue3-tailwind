<template></template>

<script setup lang="ts">
import { onMounted } from "@vue/runtime-core";
import Globe from "globe.gl";

onMounted(() => {
  const container = document.createElement("div");
  const app = document.getElementById("app")?.appendChild(container);
  const myGlobe = Globe();
  myGlobe(container).globeImageUrl("lunar.jpg");
});
</script>