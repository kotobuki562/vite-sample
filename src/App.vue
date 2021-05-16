<template>
  <!-- <img alt="Vue logo" src="./assets/logo.png" />
  <Button btnText="お歳暮" /> -->
  <TrackData />
</template>

<script lang="ts">
import { defineComponent } from "vue";
import Button from "./components/Button.vue";
import TrackData from "./components/TrackData.vue";

export default defineComponent({
  name: "App",
  components: {
    Button,
    TrackData,
  },
});
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
