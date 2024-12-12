<template>
    <div>
        <h3 :class="{ done: taskStatus }"> {{ taskTitle }}</h3>
        <button @click="$emit('toggle-task')">
            {{ taskStatus ? 'Mark as Undone' : 'Mark as Done' }}
        </button>
    </div>
</template>

<script setup>
import { defineProps, defineEmits } from 'vue';

defineProps({
    taskTitle: String,
    taskStatus: Boolean,
});

const emit = defineEmits();

</script>

<style scoped>
.done {
    text-decoration: line-through;
}
</style>