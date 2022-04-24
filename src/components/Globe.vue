<template>
  <div ref="globeContainer"></div>
</template>

<script lang="ts">
import { onMounted } from "@vue/runtime-core";
import Globe, { GlobeInstance } from "globe.gl";
import { ref } from "vue";

export default {
  props: {
    width: Number,
    heigth: Number,
  },
  setup(props) {
    const globeContainer = ref();

    onMounted(() => {
      const globe: GlobeInstance = Globe({ animateIn: true });
      globe(globeContainer.value as HTMLDivElement)
        .globeImageUrl("earth-night.jpg")
        .bumpImageUrl("earth-topology.png")
        .backgroundImageUrl("night-sky.png");
      if (props.width) {
        globe.width(props.width);
      }
      if (props.heigth) {
        globe.height(props.heigth);
      }
      (globe.controls() as any).autoRotate = true;
      (globe.controls() as any).autoRotateSpeed = 0.6;
    });

    return {
      globeContainer,
    };
  },
};
</script>