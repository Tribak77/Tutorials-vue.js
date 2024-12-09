<template>
  <div>
    <h1>To-Do List</h1>
    <input v-model="newTask" placeholder="Add a task" />
    <button @click="addTask">Add</button>
    <ul>
      <li v-for="(task, index) in tasks" :key="index">
        <span :style="{ textDecoration: task.done ? 'line-through' : 'none' }">
          {{ task.text }}
        </span>
        <button @click="toggleTask(index)">Toggle</button>
        <button @click="deleteTask(index)">Delete</button>
      </li>
    </ul>
  </div>
</template>

<script>
  export default {
    data() {
      return {
        newTask: "",
        tasks: [],
      };
    },
    methods: {
      addTask() {
        if (this.newTask.trim()) {
          this.tasks.push({ text: this.newTask, done: false });
          this.newTask = "";
        }
      },
      toggleTask(index) {
        this.tasks[index].done = !this.tasks[index].done;
      },
      deleteTask(index) {
        this.tasks.splice(index, 1);
      },
    },
  };
</script>