<script setup lang="ts">
import { nextTick, reactive, ref } from "vue";

const state = reactive({
  tabValue: "c1",
  list: [
    {
      title: "自定义 1",
      paneKey: "c1",
      icon: "dongdong",
    },
    {
      title: "自定义 2",
      paneKey: "c2",
      icon: "JD",
    },
    {
      title: "自定义 3",
      paneKey: "c3",
    },
    {
      title: "自定义 4",
      paneKey: "c4",
    },
    {
      title: "自定义 5",
      paneKey: "c5",
    },
    {
      title: "自定义 6",
      paneKey: "c6",
    },
  ],
});
</script>

<template>
  <view class="content">
    <nut-tabs
      v-model="state.tabValue"
      swipeable
      title-scroll
      :title-gutter="10"
    >
      <template #titles>
        <div class="title-list">
          <view
            v-for="item in state.list"
            :key="item.paneKey"
            class="title-item"
            :class="{ 'tabs-active': state.tabValue === item.paneKey }"
            @click="state.tabValue = item.paneKey"
          >
            <nut-icon name="dongdong" />
            <view class="nut-tabs__titles-item__text">
              {{ item.title }}
            </view>
            <view class="item__line" />
          </view>
        </div>
      </template>
      <nut-tab-pane
        v-for="item in state.list"
        :key="item.paneKey"
        title=""
        :pane-key="item.paneKey"
      >
        {{ item.title }}
      </nut-tab-pane>
    </nut-tabs>
  </view>
</template>

<style lang="scss" scoped>
.content {
  width: 100%;
  height: 100%;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
}

.title-list {
  display: flex;
  justify-content: space-around;
  align-items: center;
  width: 100%;

  .title-item {
    display: flex;
    justify-content: space-around;
    align-items: center;
    position: relative;
  }

  .tabs-active {
    font-weight: bold;
    transition: width 0.3s ease;
  }
}
</style>
