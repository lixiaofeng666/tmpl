<template>
  <div class="page">
    <div class="list">
      <div class="item" v-for="item in tasks" :key="item.id">
        <div class="item-delay" v-if="item.isDelayed">已延误</div>
        <div class="item-content">
          <div class="item-title">{{ item.title }}</div>
          <div class="item-details">
            <div class="item-detail">进度：{{ item.progress * 100 }}%</div>
            <div class="item-detail">耗时：{{ item.consumingTime }} 小时</div>
          </div>
        </div>
        <svg
          class="item-edit"
          t="1675393327492"
          viewBox="0 0 1024 1024"
          version="1.1"
          xmlns="http://www.w3.org/2000/svg"
          p-id="5098"
          width="64"
          height="64"
          @click="onEdit(item)">
          <path
            d="M895.655 411.812c-13.807 0-25 11.193-25 25v225.331c0 112.755-91.732 204.487-204.487 204.487H357.832c-112.755 0-204.487-91.732-204.487-204.487V353.806c0-112.754 91.732-204.486 204.487-204.486h212.33c13.807 0 25-11.193 25-25 0-13.808-11.193-25-25-25h-212.33c-67.723 0-131.56 26.541-179.753 74.733-48.193 48.193-74.734 112.03-74.734 179.753v308.337c0 67.723 26.541 131.56 74.734 179.753s112.03 74.734 179.753 74.734h308.336c67.723 0 131.56-26.541 179.753-74.734s74.734-112.03 74.734-179.753V436.812c0-13.807-11.192-25-25-25z"
            fill="#FF7B15"
            p-id="5099"></path>
          <path
            d="M835.27 332.703c37.216-37.216 37.216-98.115-0.001-135.332-37.215-37.216-98.114-37.216-135.331 0l-18.601 18.602 135.331 135.332 18.602-18.602zM335.87 568.063l-23.181 109.544c-5.051 23.871 18.474 47.395 42.345 42.344l109.544-23.18c8.245-1.745 24.441-17.818 27.383-20.759l301.854-301.854-135.332-135.332L356.629 540.68c-2.941 2.942-19.014 19.137-20.759 27.383z"
            fill="#FF7B15"
            p-id="5100"></path>
        </svg>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      // 模拟列表数据
      tasks: [...Array(10)].map((_, i) => {
        return {
          id: i,
          title: `日报开发${i}`,
          progress: 0.5,
          consumingTime: 2,
          isDelayed: Math.random() > 0.5
        }
      })
    }
  },
  methods: {
    // 点击编辑事件
    onEdit(item) {
      // 将列表项 id 传至详情页
      this.$router.push({
        path: '/taskDetail',
        query: {
          id: item.id
        }
      })
    }
  }
}
</script>

<style scoped>
.page {
  background: #f8f8f8;
  min-height: 100vh;
}
.list {
  padding: 16px;
}
.item {
  position: relative;
  display: flex;
  align-items: center;
  padding: 16px;
  margin-bottom: 8px;
  background: #fff;
  border-radius: 8px;
  box-shadow: 0 4px 16px #eee;
  border: 1px solid #eee;
}
.item-delay {
  position: absolute;
  z-index: 0;
  top: 8px;
  right: 8px;
  font-size: 12px;
  color: #8d0606;
}
.item-content {
  width: 0;
  flex: 1;
}
.item-title {
  font-size: 18px;
  font-weight: bold;
  color: #666;
  white-space: nowrap;
  text-overflow: ellipsis;
  overflow: hidden;
  margin-bottom: 16px;
}
.item-details {
  display: flex;
  font-size: 14px;
  color: #999;
}
.item-detail {
  margin-right: 24px;
}
.item-edit {
  width: 32px;
  height: 32px;
  margin-left: 8px;
}
</style>
