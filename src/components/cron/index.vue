<template>
  <span @click="init">
    <slot>选择</slot>
  </span>
  <el-dialog
    title="Cron表达式生成器"
    v-model="dialogVisible"
    :align-center="true"
    append-to-body
    destroy-on-close
  >
    <Crontab
      @hide="closeHand"
      @fill="crontabFill"
      :expression="modelValue"
    ></Crontab>
  </el-dialog>
</template>

<script setup lang="ts">
import { computed, ref } from "vue";
import Crontab from "./Crontab/index.vue";
const props = withDefaults(
  defineProps<{
    modelValue: any;
  }>(),
  {}
);

let dialogVisible = ref(false);
const init = () => {
  dialogVisible.value = true;
};
/** 确定后回传值 */
const crontabFill = (value: string) => {
  emits("update:modelValue", value);
};
const closeHand = () => {
  dialogVisible.value = false;
};
const emits = defineEmits(["update:modelValue"]);
</script>

<style lang="scss" scoped></style>
