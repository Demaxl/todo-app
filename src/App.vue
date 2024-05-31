<template>
    <div class="container mt-5 mb-5">
        <div class="header row gap-4">
            <div class="col">
                <h1 class="bold display-5">Good Morning, Demaxl!👋</h1>
                <h3 class="text-muted mt-2">Today, Wed 6 July 2023</h3>
            </div>
            <div class="col-md-6">
                <div class="d-flex date-container justify-content-md-end">
                    <div class="date d-flex align-items-center bg-light p-3 rounded-3 me-2 my-auto">
                        <span
                            class="chevron rounded-3 p-1 bold"
                            uk-icon="icon: chevron-down; ratio: 1.5"
                        ></span>
                        <span class="ps-3 pe-5 bold">Today</span>
                    </div>
                    <div class="bg-light p-3 rounded-3 d-flex align-items-center">
                        <span uk-icon="icon: menu; ratio: 1.5"></span>
                    </div>
                </div>
            </div>
        </div>
        <TodoList :tasks="tasks" />

        <div class="create-task-container d-flex flex-column justify-content-center mt-5">
            <TodoItemCreate v-show="showTaskCreateContainer" @taskCreateEvent="createTodoItem" />

            <button
                class="btn btn-dark p-2 px-3 rounded-5 mt-4 w-50 mx-auto"
                @click="showTaskCreateContainer = !showTaskCreateContainer"
            >
                <span class="me-2" uk-icon="icon: plus"></span>Create new task
            </button>
        </div>
    </div>
</template>

<script>
import TodoList from './components/TodoList.vue'
import TodoItemCreate from './components/TodoItemCreate.vue'

export default {
    name: 'App',
    components: { TodoList, TodoItemCreate },
    data() {
        return {
            showTaskCreateContainer: true,
            tasks: [
                {
                    id: 1,
                    title: 'Jogging',
                    startDateTime: new Date('2024T06:00:00'),
                    endDateTime: new Date('2024T07:30:00'),
                    isComplete: true
                },
                {
                    id: 2,
                    title: 'Read a book',
                    startDateTime: new Date('2024T08:00:00'),
                    endDateTime: new Date('2024T09:00:00'),
                    isComplete: false
                },
                {
                    id: 3,
                    title: 'Wireframing a new product',
                    startDateTime: new Date('2024T09:00:00'),
                    endDateTime: new Date('2024T11:00:00'),
                    isComplete: true
                }
                // {
                //     id: 3,
                //     title: 'Lorem, ipsum dolor sit amet consectetur adipisicing elit. Modi blanditiis asperiores quas, officia, veniam amet tempora saepe corrupti tempore error rem quo ea delectus earum eos magnam nostrum dolore hic. Sequi quibusdam reiciendis voluptatibus non ipsam error dolorem minima explicabo quae tenetur mollitia perferendis itaque fugiat, nulla doloremque ducimus impedit?',
                //     startDateTime: '12:00',
                //     endDateTime: '18:00',
                //     isComplete: true
                // }
            ]
        }
    },
    methods: {
        createTodoItem(title, startDateTime, endDateTime) {
            this.tasks.push({
                id: this.tasks.length + 1,
                title: title,
                startDateTime: startDateTime,
                endDateTime: endDateTime,
                isComplete: false
            })
        }
    }
}
</script>

<style lang="scss">
@import url('https://fonts.googleapis.com/css2?family=Poppins:ital,wght@0,100;0,200;0,300;0,400;0,500;0,600;0,700;0,800;0,900;1,100;1,200;1,300;1,400;1,500;1,600;1,700;1,800;1,900&display=swap');

$background-color: #f4f4f4;

* {
    box-sizing: border-box;
}

html,
body {
    font-family: 'Poppins', sans-serif;
    background-color: $background-color;
}

.bold {
    font-weight: bold;
}

.header {
    .date-container {
        height: 50px !important;
    }
    .date {
        height: 50px;
        .chevron {
            background-color: $background-color;
        }
    }
}
</style>
