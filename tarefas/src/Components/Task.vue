<template>
    <div 
    @click="$emit('taskStateChanged', task)"
    class="task" :class="stateClass">
        <span @click.stop="$emit('taskDeleted', task)" class="close">x</span>
        <p>{{ task.name }}</p>
    </div>
</template>

<script>
export default {
    props: { 
        task: { type: Object, required: true }
    },
    computed: {
        stateClass() {
            return {
                pending: this.task.pending,
                done: !this.task.pending
            }
        }
    }

}
</script>

<style>
.pending .close{
    background-color: #b73229;
}
.done .close {
    background-color: #0abf08 ;
}
.close {
    position: absolute;
    right: 10px;
    top: 10px;
    font-size: 0.9rem;
    height: 20px;
    width: 20px;
    border-radius: 10px;
    display: flex;
    justify-content: center;
}

</style>