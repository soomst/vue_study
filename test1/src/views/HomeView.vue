<template>
  <div>
    <h1>This is Home Page</h1>
    <!-- <form action=""> -->
    <InputField v-model="name" />
    <button @click="updateName">Submit</button>
    <!-- </form> -->
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
      name: "Soom Coder",
    };
  },

  beforeCreate() {
    console.log("beforeCreate", this.name);
  },
  created() {
    //여기서부터 데이터에 접근 가능
    console.log("created", this.name);
  },
  beforeMount() {
    //dom mount전
    alert("beforeMount", this.name);
  },
  mounted() {
    //dom을 컨트롤 하고 싶으면 여기서부터
    alert("mounted", this.name);
  },
  beforeUpdate() {
    //데이터가 업데이트 되기 전
    alert("beforeUpdate : " + this.name);
  },
  updated() {
    //데이터가 업데이트 된 후
    alert("updated : " + this.name);
  },
  beforeDestroy() {
    // 메모리 누수를 방지하기 위해 eventlistner 삭제 및 데이터 초기화 작업을 함
    alert("beforeDestroy : " + this.name);
  },
  destroyed() {
    alert("destroyed : " + this.name);
  },
  methods: {
    updateName() {
      this.name = "hello";
    },
  },
};
</script>

<style scoped>
h1 {
  color: brown;
}
</style>
