<template>
    <div>
        <TaskItem 
        v-for="task in tasks"
        :key="task.id"
        :taskTitle="task.title"
        :taskStatus="task.status"
        @toggle-task="() => toggleTask(task.id)"
        />
    </div>
</template>

<script setup>
import { defineProps, defineEmits } from 'vue';
import TaskItem from './TaskItem.vue';

const props =defineProps({
    tasks: Array,
});

const emit = defineEmits();

function toggleTask(taskId) {
    emit('toggle-task', taskId);
}
</script>