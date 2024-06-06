<template>
  <HeadComponent />
  <MainComponent />
</template>

<script>
import HeadComponent from "@/components/HeadComponent";
import MainComponent from "@/components/MainComponent";

export default {
  name: "FirstPage",
  components: {
    HeadComponent,
    MainComponent,
  },
};
</script>

<style lang="scss" scoped></style>
