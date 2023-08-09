<!--
 * @Author: linwenli@travelsky.com.cn
 * @Date: 2023-07-12 15:42:29
 * @LastEditors: linwenli@travelsky.com.cn
 * @LastEditTime: 2023-08-08 14:11:15
 * @FilePath: /toDoListOfDemo/src/App.vue
 * @Description: 这是默认设置,请设置`customMade`, 打开koroFileHeader查看配置 进行设置: https://github.com/OBKoro1/koro1FileHeader/wiki/%E9%85%8D%E7%BD%AE
-->

<script setup lang="ts">
import { RouterLink, RouterView } from "vue-router";
import { ref } from "vue";
import InputOfToDo from "./components/InputOfToDo/index.vue";
import ListOfToDo from "./components/ListOfToDo/index.vue";
import "./App.less";

const list = ref<string[]>([]);

const onSubmit = (val: string) => {
  // console.log(val, "===");

  const nextList = [...list.value];
  nextList.push(val);
  list.value = nextList;
};

const onDel = (index: number) => {
  console.log(index, "del");
  const newList = [...list.value];
  newList.splice(index, 1);
  list.value = newList;
};
</script>

<template>
  <div class="box">
    <h1>ToDoListDemo Of Vue3</h1>
    <InputOfToDo :onSubmit="onSubmit" />
    <ListOfToDo :list="list" :onDelete="onDel" />
  </div>
</template>
