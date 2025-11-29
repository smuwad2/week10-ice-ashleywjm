<script setup>
    import TaskTracker from "./subcomponents/TaskTracker.vue";
</script>

<script>
    export default {
        data() {
            return {
                desc: '',
                deadline: '',
                taskList: []
            }
        },
        components: { TaskTracker },
        methods: {
            add() {
                this.taskList.push( { 'desc': this.desc, 'deadline': this.deadline } )
                this.desc = ''
                this.deadline = ''
            },
            // TODO: Add a new method, to delete a task completed
            removeTask(idx) {
                this.taskList.splice(idx, 1);
            } 
        }
    }

</script>

<template>
    <div class="mb-3">
        <label for="desc" class="form-label">Task</label>
        <input type="text" class="form-control" id="desc" v-model='desc' placeholder="task">
    </div>
    <div class="mb-3">
        <label for="deadline" class="form-label">Deadline</label>
        <input type="date" class="form-control" id="deadline" v-model='deadline' placeholder="deadline">
    </div>

    <button type="button" @click="add" class="btn btn-primary">Add New Task</button>
    <hr>

    <!-- TODO: Modify following code -->
    <task-tracker 
        v-for="(t, i) in taskList"
        :key="i"
        :task="t"
        :idx="i"
        @done="removeTask"
    ></task-tracker>

</template>

<style scoped>
    @media (min-width: 768px) {
    .card { width: 48%; display: inline-block; margin-right: 2%; vertical-align: top; }
    .card:nth-child(2n) { margin-right: 0; }
    }
</style>
