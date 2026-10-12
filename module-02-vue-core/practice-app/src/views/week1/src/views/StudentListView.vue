<template>
  <div class="student-list">
    <ul class="list">
      <li v-for="(student, index) in students" :key="index" class="student-item">
        <span>{{ student.name }} ({{ student.id }}) - 成绩: {{ student.score }}</span>
        <button @click="removeStudent(index)" class="delete-btn">删除</button>
      </li>
    </ul>

    <!-- 统计信息 -->
    <div class="stats">
      总人数: {{ students.length }} | 平均成绩: {{ averageScore.toFixed(1) }}
    </div>
  </div>
</template>

<script setup>
// 不需要 lang="ts"，直接用 JS
import { ref, computed } from 'vue'

// 学生数据（用 JS 对象定义，不加类型）
const students = ref([
  { name: '张三', id: '2021001', score: 85 },
  { name: '李四', id: '2021002', score: 92 },
])

// 计算平均成绩
const averageScore = computed(() => {
  if (students.value.length === 0) return 0
  const total = students.value.reduce((sum, s) => sum + s.score, 0)
  return total / students.value.length
})

// 删除学生
const removeStudent = (index) => {
  students.value.splice(index, 1)
}

</script>

<style scoped>
.student-list {
  max-width: 600px;
  margin: 20px auto;
  padding: 20px;
  border: 1px solid #ddd;
  border-radius: 8px;
}

.list {
  list-style: none;
  padding: 0;
}

.student-item {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 10px;
  border-bottom: 1px solid #eee;
}

.delete-btn {
  background: #ff4d4f;
  color: white;
  border: none;
  padding: 5px 10px;
  border-radius: 4px;
  cursor: pointer;
}

.stats {
  margin-top: 20px;
  font-weight: bold;
  color: #666;
}
</style>
