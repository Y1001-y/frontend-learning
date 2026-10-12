<!-- <script setup>
import { ref } from 'vue'

// 海报A
const posterA = {
  title: '2026 春季校园歌手大赛',
  status: 'signing',
  cover: 'https://infinityx7-oss.oss-cn-hangzhou.aliyuncs.com/img/sing1.png',
  offline: false
}

// 海报B
const posterB = {
  title: '校园街舞挑战赛',
  status: 'closed',
  cover: 'https://infinityx7-oss.oss-cn-hangzhou.aliyuncs.com/img/sing2.png',
  offline: false
}

// 当前活动
const activity = ref({
  title: '2026 春季校园歌手大赛',
  status: 'signing',
  cover: 'https://infinityx7-oss.oss-cn-hangzhou.aliyuncs.com/img/sing1.png',
  offline: false
})

// 切换标记，只用布尔值，不用数组
const isA = ref(true)

function next() {
  isA.value = !isA.value
  activity.value = isA.value ? posterA : posterB
}

function prev() {
  isA.value = !isA.value
  activity.value = isA.value ? posterA : posterB
}

// 下架功能
function takeDown() {
  activity.value = {
    title: activity.value.title,
    status: 'closed',
    cover: activity.value.cover,
    offline: true
  }
}
</script>

<template>
  <div class="container">
    <div class="poster-wrap">
      <button class="switch-btn" @click="prev">上一张</button>

      <article class="activity-card">
        <img :src="activity.cover" :alt="activity.title" class="card-poster" />
        <div class="card-body">
          <h3 class="card-title">{{ activity.title }}</h3>

          <span class="tag"
            :class="{
              'tag--draft': activity.status === 'draft',
              'tag--signing': activity.status === 'signing',
              'tag--closed': activity.status === 'closed',
              'tag--finished': activity.status === 'finished'
            }"
          >
            {{
              activity.status === 'draft' ? '草稿' :
              activity.status === 'signing' ? '报名中' :
              activity.status === 'closed' ? '已截止' : '已结束'
            }}
          </span>

          <button
            class="card-btn"
            :disabled="activity.status !== 'draft'"
            @click="takeDown"
          >
            下架
          </button>
        </div>
      </article>

      <button class="switch-btn" @click="next">下一张</button>
    </div>
  </div>
</template>

<style scoped>
.container {
  width: 80%;
  margin: 60px auto 0;
}

.poster-wrap {
  display: flex;
  align-items: center;
  gap: 16px;
}

.activity-card {
  width: 320px;
  background: #fff;
  border-radius: 16px;
  overflow: hidden;
  box-shadow: 0 4px 18px rgba(0,0,0,0.12);
  transition: transform 0.25s ease, box-shadow 0.25s ease;
}

.activity-card:hover {
  transform: translateY(-4px);
  box-shadow: 0 8px 24px rgba(0,0,0,0.16);
}

.card-poster {
  width: 100%;
  height: 320px;
  object-fit: cover;
  display: block;
}

.card-body {
  padding: 16px;
}

.card-title {
  margin: 0 0 12px;
  font-size: 18px;
  font-weight: 600;
  color: #222;
}

.tag {
  display: inline-block;
  padding: 4px 10px;
  font-size: 12px;
  border-radius: 999px;
  background: #eee;
  color: #666;
}

.tag--signing {
  background: #ec4899;
  color: #fff;
}

.tag--closed {
  background: #6b7280;
  color: #fff;
}

.tag--draft {
  background: #3b82f6;
  color: #fff;
}

.tag--finished {
  background: #10b981;
  color: #fff;
}

.card-btn {
  margin-top: 14px;
  padding: 6px 14px;
  border-radius: 8px;
  border: none;
  background: #333;
  color: #fff;
  cursor: pointer;
}

.card-btn:disabled {
  background: #cccccc;
  cursor: not-allowed;
}

.switch-btn {
  padding: 8px 12px;
  border-radius: 8px;
  border: 1px solid #ddd;
  background: #fff;
  cursor: pointer;
}

.switch-btn:hover {
  background: #f3f4f6;
}
</style> -->

<template>
  <div id="app">
    <!-- 直接使用 StudentList 组件 -->
    <StudentList />
  </div>
</template>

<script setup>
// ✅ 无需 import StudentList，<script setup> 会自动注册同目录下的组件
// 如果你想让代码更清晰，也可以显式导入：
// import StudentList from './components/StudentList.vue'
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
