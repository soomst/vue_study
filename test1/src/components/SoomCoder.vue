<template>
  <div>
    <h1>{{ title }}</h1>
    <p>{{ name }}</p>
    <button @click="updateName">Change Name</button>
  </div>
</template>

<script>
export default {
  //props: ["title"],
  props: {
    title: {
      type: String,
      required: true,
      default: "default Tiltle",
    },
    name: {
      type: String,
      default: "default name",
    },
  },
  data() {
    return {
      // name: "Soom Coder",
    };
  },
  methods: {
    updateName() {
      //this.name = "Soom Coder updated";
    },
  },
};
</script>

<style scoped></style>
