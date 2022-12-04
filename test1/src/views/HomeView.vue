<template>
  <div>
    <h1>This is Home Page</h1>
    <soomCoder />
  </div>
</template>

<script>
import soomCoder from "@/components/SoomCoder.vue";

export default {
  components: {
    soomCoder,
  },
  data() {
    return {
      name: "soom coder",
    };
  },
};
</script>

<style scoped>
h1 {
  color: brown;
}
</style>
