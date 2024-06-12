<template>
  <FirstPage />
</template>

<script>
import FirstPage from "./pages/FirstPage";

export default {
  name: "App",
  components: { FirstPage },
};
</script>

<style lang="scss">
*,
*:before,
*:after {
  -moz-box-sizing: border-box;
  -webkit-box-sizing: border-box;
  box-sizing: border-box;
}

body {
  margin: 0;
  background-color: #fafafa;
}

.center {
  display: flex;
  justify-content: center;
  align-items: center;
}
</style>