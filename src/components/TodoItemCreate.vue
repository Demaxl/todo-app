<template>
    <form class="mx-sm-auto" @submit.prevent="createTask">
        <div class="d-flex flex-column">
            <div class="mb-3">
                <input
                    type="text"
                    class="form-control title-input rounded-3 py-23"
                    name="title"
                    id="title"
                    v-model="taskTitle"
                    aria-describedby="helpId"
                    placeholder="Task title"
                />
            </div>

            <div class="d-flex flex-column flex-sm-row gap-4 justify-content-center">
                <VueDatePicker
                    v-model="startDateTime"
                    v-bind="datePickerProps"
                    :min-date="new Date()"
                    ignore-time-validation
                />
                <VueDatePicker
                    v-model="endDateTime"
                    v-bind="datePickerProps"
                    placeholder="Select end date and time"
                    :min-date="startDateTime"
                />
            </div>
            <div class="mt-3 d-grid">
                <input
                    type="submit"
                    value="Save changes"
                    class="btn d-block btn-primary rounded-4 px-3"
                />
            </div>
        </div>
    </form>
</template>

<script>
import VueDatePicker from '@vuepic/vue-datepicker'
import '@vuepic/vue-datepicker/dist/main.css'

export default {
    name: 'TodoItemCreate',
    components: { VueDatePicker },
    data() {
        return {
            startDateTime: null,
            endDateTime: null,
            taskTitle: null,
            datePickerProps: {
                'partial-flow': true,
                placeholder: 'Select start date and time',
                // 'time-picker-inline': true,
                'input-class-name': 'dp-custom-input bg-dark text-light rounded-4 py-2',
                'menu-class-name': 'dp-custom-menu',
                required: true,
                dark: true,
                'auto-apply': true,
                flow: ['hours', 'minutes', 'calendar']
            }
        }
    },
    // mounted() {
    //     this.startDateTime = null
    //     this.endDateTime = null
    //     this.taskTitle = null
    // },
    methods: {
        createTask() {
            this.$emit('taskCreateEvent', this.taskTitle, this.startDateTime, this.endDateTime)
            this.startDateTime = null
            this.endDateTime = null
            this.taskTitle = null
        }
    }
}
</script>

<style lang="scss" scoped>
@import 'src/assets/scss/variables.scss';

.dp__flex_display_with_input {
    align-items: unset !important;
}

.dp-custom-menu {
    margin-bottom: 15px;
    padding: 10px;
    border-radius: 15px;
}

.title-input {
    background-color: $background-color;
    border: none;

    &:focus {
        background-color: $background-color;
    }
}

form {
    background-color: white;
    border-radius: 15px;
    padding: 15px;
    box-shadow: 0 0 5px 0 rgba(0, 0, 0, 0.1);

    input:focus {
        box-shadow: none !important;
    }
}
</style>
