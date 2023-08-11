<script setup>
import "./index.less";
import { Delete } from "@element-plus/icons-vue";
const props = defineProps(["list", "onDelete"]);
// console.log(props.list, "===list.value");
</script>

<template>
  <div class="listOfToDo">
    <ol>
      <li v-for="(item, index) in props.list" key="index">
        <div>
          <span>{{ item }}</span>
          <el-button
            type="text"
            :icon="Delete"
            plain
            @click="onDelete(index)"
          />
        </div>
      </li>
    </ol>
    <div class="noData" v-if="list?.length <= 0">暂无数据</div>
  </div>
</template>
