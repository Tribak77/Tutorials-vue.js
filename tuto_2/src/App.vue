<template>
  <Header>
    <template #title>
      <h1>My To-Do List</h1>
    </template>
  </Header>

  <TaskList :tasks="tasks" @toggle-task="toggleTask" />

  <Footer />
</template>

<script setup>
import Header from './components/header.vue';
import Footer from './components/Footer.vue';
import TaskList from './components/TaskList.vue';
import { reactive } from 'vue';

const tasks = reactive([
  { id: 1, title: 'Learn Vue', status: false },
  { id: 2, title: 'Build a project', status: true },
]);

function toggleTask(taskId) {
  const task = tasks.find((t) => t.id === taskId);
  if (task) task.status = !task.status;
}
</script>
