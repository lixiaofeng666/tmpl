<template>
  <div>接收到id:{{ taskId }}</div>
</template>

<script>
export default {
  data() {
    return {
      taskId: ''
    }
  },
  created() {
    this.taskId = this.$route.query.id
  }
}
</script>
