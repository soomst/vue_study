<template>
  <div class="about">
    <h1>This is an about page</h1>
    <soomCoder>
      <!-- <template v-slot:header> -->
      <!-- <template #header="props"> -->
      <template #header="{ soom }">
        {{ soom }}
        <h1>header1</h1>
      </template>
      <template v-slot:default> <h3>hello1</h3> </template>
    </soomCoder>
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
