<template lang="">
    <div class="todo-container mx-3 mt-5">
        <TodoItem
            v-for="task in tasks"
            :key="task.id"
            v-bind="task"
            @taskCompleteEvent="taskComplete($event, task)"
        />
    </div>
</template>

<script>
import TodoItem from './TodoItem.vue'

export default {
    components: { TodoItem },
    data() {
        return {
            tasks: [
                {
                    id: 1,
                    title: 'Jogging',
                    startTime: '06:00',
                    endTime: '07:30',
                    isComplete: true
                },
                {
                    id: 2,
                    title: 'Read a book',
                    startTime: '08:00',
                    endTime: '09:00',
                    isComplete: false
                },
                {
                    id: 3,
                    title: 'Wireframing a new product',
                    startTime: '09:00',
                    endTime: '11:00',
                    isComplete: true
                },
                {
                    id: 3,
                    title: 'Lorem, ipsum dolor sit amet consectetur adipisicing elit. Modi blanditiis asperiores quas, officia, veniam amet tempora saepe corrupti tempore error rem quo ea delectus earum eos magnam nostrum dolore hic. Sequi quibusdam reiciendis voluptatibus non ipsam error dolorem minima explicabo quae tenetur mollitia perferendis itaque fugiat, nulla doloremque ducimus impedit?',
                    startTime: '12:00',
                    endTime: '18:00',
                    isComplete: true
                }
            ]
        }
    },
    methods: {
        taskComplete(event, task) {
            task.isComplete = !task.isComplete
        }
    }
}
</script>

<style lang="scss"></style>
