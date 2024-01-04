<template>
  <view class="content">
    <nut-button type="primary" @click="state.showDate = true"
      >打开日历</nut-button
    >
    <div>{{ state.date }}</div>
    <nut-calendar
      ref="calendarRef"
      v-model:visible="state.showDate"
      type="range"
      title="入库时间"
      :default-value="state.defaultDate"
      @choose="dateChoose"
      start-date="2022-01-01"
      end-date="2024-01-04"
      is-auto-back-fill
      show-today
    />
  </view>
</template>
<script setup lang="ts">
import { ref, reactive } from "vue";

const title = ref("Hello");

const state = reactive({
  showDate: false,
  date: [] as any,
  defaultDate: ["2024-01-01", "2024-01-03"],
});

const dateChoose = (val: any) => {
  console.log(val);
  state.date = val;
};
</script>

<style>
.content {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
}

.logo {
  height: 200rpx;
  width: 200rpx;
  margin-top: 200rpx;
  margin-left: auto;
  margin-right: auto;
  margin-bottom: 50rpx;
}

.text-area {
  display: flex;
  justify-content: center;
}

.title {
  font-size: 36rpx;
  color: #8f8f94;
}
</style>
