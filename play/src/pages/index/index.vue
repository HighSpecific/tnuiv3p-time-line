<script setup lang="ts">
import TnTimeLine from '../../packages/src/time-line.vue'
import TnTimeLineItem from '../../packages/src/time-line-item.vue'
import TnTimeLineData from '../../packages/src/time-line-data.vue'

interface TimeLineDataItem {
  date?: string
  version?: string
  content: string
}

interface TimeLineData {
  month: string
  icon?: string
  data: TimeLineDataItem[]
}

// 时间轴数据
const timeLineData: TimeLineData[] = [
  {
    month: '2023-07',
    icon: 'moments',
    data: [
      {
        date: '1',
        version: '1.0.0',
        content:
          '图鸟科技，图鸟UI vue3 uniapp版本全新发布，欢迎各位开发者进行使用',
      },
      {
        content:
          '图鸟科技，图鸟UI vue3 uniapp版本全新发布，欢迎各位开发者进行使用',
      },
    ],
  },
  {
    month: '2023-08',
    icon: 'creative',
    data: [
      {
        content:
          '图鸟科技，图鸟UI vue3 uniapp版本全新发布，欢迎各位开发者进行使用',
      },
      {
        date: '2',
        version: '1.0.0',
        content:
          '图鸟科技，图鸟UI vue3 uniapp版本全新发布，欢迎各位开发者进行使用',
      },
    ],
  },
]
</script>

<template>
  <view class="content">
    <TnTimeLine>
      <TnTimeLineItem
        v-for="(item, index) in timeLineData"
        :key="index"
        :title="item.month"
        :title-icon="item.icon ?? ''"
      >
        <template #title>
          <view class="tn-flex tn-w-full justify-between">
            <view>1</view>
            <view>2</view>
          </view>
        </template>
        <TnTimeLineData
          v-for="(dataItem, dataIndex) in item.data"
          :key="dataIndex"
        >
          <view
            v-if="dataItem?.date"
            class="time-line__title tn-flex justify-between items-center tn-gray-dark_text"
          >
            <view class="date">{{ dataItem?.date || '' }}</view>
            <view class="version">{{ dataItem?.version || '' }}</view>
          </view>
          <view class="time-line__data">
            {{ dataItem.content }}
          </view>
        </TnTimeLineData>
      </TnTimeLineItem>
    </TnTimeLine>
  </view>
</template>

<style lang="scss" scoped>
.content {
  position: relative;
  width: 100%;
  padding: 30rpx;

  .time-line {
    &__title {
      font-size: 32rpx;
      margin-bottom: 20rpx;
    }
  }
}
</style>
