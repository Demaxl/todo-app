<template lang="">
    <div class="todo-container mx-3 mt-5">
        <TodoItem
            v-for="task in tasks"
            :key="task.id"
            v-bind="task"
            @taskCompleteEvent="taskComplete($event, task)"
            @taskDeleteEvent="this.$emit('taskDeleteEvent', task)"
        />
    </div>
</template>

<script>
import TodoItem from './TodoItem.vue'

export default {
    components: { TodoItem },
    props: ['tasks'],
    data() {
        return {}
    },
    methods: {
        taskComplete(event, task) {
            task.isComplete = !task.isComplete
            this.$emit('taskChangedEvent')
        }
    }
}
</script>

<style lang="scss"></style>
