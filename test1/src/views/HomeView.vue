<template>
  <div>
    <h1>This is Home Page</h1>
    <form action="">
      <InputField v-model="name" />
      <button>Submit</button>
    </form>
    {{ name }}
  </div>
</template>

<script>
import InputField from "@/components/InputField.vue";

export default {
  components: {
    InputField,
  },
  data() {
    return {
      name: "",
    };
  },
  // methods: {
  //   updateName(name) {
  //     this.name = name;
  //   },
  // },
};
</script>

<style scoped>
h1 {
  color: brown;
}
</style>
