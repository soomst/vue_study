<template>
  <div>
    <label for="">Name</label>
    <input
      type="text"
      :value="name"
      style="padding: 30px; border: 2px solid green"
      @input="updateName"
    />
    <!-- @input : input 태그에 입력 일어나면 updateName 메소드 실행 -->
  </div>
</template>

<script>
export default {
  props: {
    name: {
      type: String,
      required: true,
    },
  },
  methods: {
    updateName(e) {
      // 부모 컴포넌트로 이벤트를 보내줌
      this.$emit("update-name", e.target.value);
    },
  },
};
</script>
