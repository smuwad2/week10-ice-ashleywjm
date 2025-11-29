<script>
    // TODO: Complete the code
    export default { 
        data() {
            return {

            }
        },
        // Hint: insert properties task (Object) and idx (Number)
        props: {
            task: { type: Object, required: true }, // { desc, deadline }
            idx:  { type: Number, required: true }
        },
        methods: {
            markDone() {
            // tell parent which index to remove
            this.$emit("done", this.idx);
            }
        }
    }
</script>

<template>
    <!-- TODO: add your template code here --> 
     <div class="card mb-3">
        <div class="card-body text-center">
        <h6 class="text-muted mb-2">Deadline: {{ task.deadline || "—" }}</h6>
        <hr class="my-2" />
        <p class="card-text">{{ task.desc }}</p>
        <button class="btn btn-primary btn-sm" @click="markDone">Done</button>
        </div>
    </div>
   
</template>


