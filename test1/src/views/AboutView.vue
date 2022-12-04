<template>
  <div class="about">
    <h1>This is an about page</h1>
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
