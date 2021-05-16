<template>
  <button class="btn" @click="pop">{{ btnText }}</button>
</template>

<script>
import { defineComponent } from "vue";
export default defineComponent({
  name: "Button",
  props: {
    btnText: {
      type: String,
    },
  },
  setup: () => {
    const pop = () => {
      alert("click");
    };
    return { pop };
  },
});
</script>

<style>
.btn {
  background-color: #42b983;
  color: white;
  outline: none;
  border-radius: 30px;
  border: 2px solid #42b983;
  cursor: pointer;
  padding: 5px 10px;
}
.btn:hover {
  background-color: white;
  color: #42b983;
}
</style>
