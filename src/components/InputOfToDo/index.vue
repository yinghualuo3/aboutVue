<script setup>
import { ref } from "vue";
import "./index.less";

const input = ref(null);
const props = defineProps(["onSubmit"]);

const onClick = () => {
  // console.log(input.value);
  if (input.value === null) {
    ElMessage({
      message: "输入提交不允许为空",
      type: "warning",
    });
  } else {
    props.onSubmit(input.value);
    input.value = null;
  }
};

const onKeyDown = (e) => {
  if (e.keyCode === 13) {
    input.value = e.target.value;
    onClick();
  }
};
</script>

<template>
  <div class="inputOfToDo">
    <el-input
      placeholder="请输入内容"
      size="small"
      v-model="input"
      clearable
      @keydown="onKeyDown"
    />
    <el-button type="primary" @click="onClick">提交</el-button>
  </div>
</template>
<!-- @keyup.enter="(onClick)" 也可以 -->
