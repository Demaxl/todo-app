<template lang="">
    <div class="todo-container mx-3 mt-5">
        <TransitionGroup name="todolist">
            <TodoItem
                v-for="task in tasks"
                :key="task.id"
                v-bind="task"
                @taskCompleteEvent="taskComplete($event, task)"
                @taskDeleteEvent="this.$emit('taskDeleteEvent', task)"
            />
        </TransitionGroup>
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

<style lang="scss">
.todolist-move, /* apply transition to moving elements */
.todolist-enter-active,
.todolist-leave-active {
    transition: all 0.5s ease;
}

.todolist-enter-from,
.todolist-leave-to {
    opacity: 0;
    transform: translateY(30px);
}

/* ensure leaving items are taken out of layout flow so that moving
   animations can be calculated correctly. */
.todolist-leave-active {
    position: absolute;
}
</style>
