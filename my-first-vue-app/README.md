# Day 1: Introduction to Vue.js  

## Objective  
Understand the basics of Vue.js and set up your development environment.

---

## Activities  

### 1. Learn About Vue.js Features and Ecosystem  
- **Read the Vue.js Introduction**  
- Understand what makes Vue.js unique:  
  - Reactive data binding.  
  - Component-based architecture.  
  - Progressive adoption (for small or large projects).  
  - Integration with tools like Vue Router and Pinia.  

---

### 2. Set Up Your Development Environment  

#### Install Node.js  
- Download [Node.js](https://nodejs.org) if it’s not already installed.

#### Choose a Project Setup Method  

**Using Vue CLI:**  
```bash
npm install -g @vue/cli
vue create my-first-vue-app
cd my-first-vue-app
npm run serve
```

**Using Vite (Recommended for Speed):**  
```bash
npm create vite@latest my-first-vue-app --template vue
cd my-first-vue-app
npm install
npm run dev
```

---

### 3. Learn Vue.js Basics  

#### Explore Vue Templates  
- Learn syntax for:
  - HTML.
  - Directives.
  - Data binding.  
- Read the [Vue Essentials Guide](https://vuejs.org/guide/essentials/).  

#### Practice Directives  
- **`v-bind`:** Dynamically bind attributes.  
- **`v-model`:** Two-way data binding.  
- **`v-for`:** Render lists.  
- **`v-if/v-else`:** Conditional rendering.  

#### Understand Event Handling  
Example:  
```html
<button @click="handleClick">Click Me</button>
```

---

### 4. Build a Simple “To-Do List” App  

#### Features  
- Add new tasks.  
- Mark tasks as complete/incomplete.  
- Delete tasks.  

#### Example Code  

**Template:**  
```vue
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
```

**Script:**  
```vue
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
```
