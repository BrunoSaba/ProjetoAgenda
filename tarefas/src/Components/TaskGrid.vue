<template>
    <div class="task-grid">
        <template>
            <Task v-for="task in tasks" :key="task.name" :task="task"></Task>
        </template>
        <p class="no-task"></p>
    </div>
</template>

<script>
import Task from './Task'
export default {
    components: {Task},
    props: {
        tasks: {type: Array, required: true }
    }

}
</script>

<style>
    .task-grid {
        display: flex;
        justify-content: center;
        flex-wrap: wrap;
    }
    .task-grid .task {
        margin: 10px;
    }

    .no-task {
        margin: 10px;
    }

    .task {
        box-sizing: border-box;
        height: 150px;
        width: 350px;
        display: flex;
        justify-content: center;
        border-radius: 8px;
        align-items: center;
        padding: 5px;
        margin-top: 4px;
        cursor: pointer;
        user-select: none;
    }
    .pending {
        background: linear-gradient(to bottom, #333333, #dd1818);
        border-left: 12px solid rgb(114, 32, 32); 
    }
    .done {
        background: linear-gradient(to right, #799f0c, #acbb78);
        border-left: 12px solid rgb(17, 75, 17);
    }

</style>