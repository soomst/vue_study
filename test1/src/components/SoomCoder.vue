<template>
  <div>
    <p>{{ name }}</p>
    <button @click="updateName">Change Name</button>
  </div>
</template>

<script>
export default {
  data() {
    return {
      name: "Soom Coder",
    };
  },
  methods: {
    updateName() {
      this.name = "Soom Coder updated";
    },
  },
};
</script>

<style scoped></style>
