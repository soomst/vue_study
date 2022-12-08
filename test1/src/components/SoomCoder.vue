<template>
  <div>
    <p>header</p>
    <slot name="header" :soom="soom"></slot>
    <p>body</p>
    <slot></slot>
    <p>footer</p>
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
      soom: "coder",
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
