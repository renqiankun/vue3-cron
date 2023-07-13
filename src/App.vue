<template>
  <el-input v-model="form.cronExpression" placeholder="请输入CRON 表达式">
    <template #append>
      <caron v-model="form.cronExpression">
        <el-button type="primary">
          生成表达式2
          <i class="el-icon-time el-icon--right"></i>
        </el-button>
      </caron>
    </template>
  </el-input>
</template>
<script setup lang="ts">
import { ref } from "vue";
import caron from "./components/cron/index.vue";
// 表单参数
const form = ref({
  cronExpression: "",
});
</script>
<style scoped></style>
