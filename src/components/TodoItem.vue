<template>
    <div
        class="todo-item py-2 px-sm-3 d-flex flex-column gap-3 flex-sm-row shadow-sm mb-2 row bg-light rounded-3"
    >
        <div
            ref="todoCheckContainer"
            class="todo-check-container col form-check form-check-inline d-flex justify-content-center justify-content-sm-start align-items-center"
        >
            <input
                :class="{ 'todo-complete-check': isComplete }"
                class="form-check-input todo-check rounded-3 me-3"
                type="checkbox"
                id="inlineCheckbox1"
                value="option1"
                :checked="isComplete"
                @change="this.$emit('taskCompleteEvent')"
            />
            <label class="form-check-label line-above" for="inlineCheckbox1"
                ><span>{{ title }}</span></label
            >
        </div>
        <div
            class="col p-0 d-flex align-items-center justify-content-center todo-time-container justify-content-md-end"
        >
            <div class="todo-time text-center me-2 py-2 px-3 rounded-3">
                <span class="" uk-icon="icon: clock"></span>
                {{ startTime }} - {{ endTime }}
            </div>
            <div class="p-2 rounded-3">
                <span uk-icon="icon: more-vertical"></span>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    props: ['title', 'startTime', 'endTime', 'isComplete'],
    data() {
        return {}
    },
    methods: {}
}
</script>

<style lang="scss">
.todo-check {
    width: 30px !important;
    height: 30px !important;
    border-color: #ccc;
    border-width: 1.5px;
    transition: background-color 0.5s;

    &:checked {
        background-color: black;
        border-color: #ccc;
    }
    & + label {
        text-decoration: line-through;
        text-decoration-color: transparent;
        transition-property: text-decoration-color;
        transition-duration: 0.5s;
        transition-delay: 0.1s;
    }

    &:checked + label {
        text-decoration-color: black;
    }

    &:focus {
        border-color: #ccc;
        outline: 2px solid black;
        outline-offset: 3px;
        box-shadow: none;
    }
}

.todo-time-container > div {
    background-color: #f3f3f3;
}

.todo-time {
    width: 170px;
}
</style>
