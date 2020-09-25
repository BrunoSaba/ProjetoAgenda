<template>
    <div class="new-task">
        <input v-model="name" @keydown.enter="add" type="text" class="form-element" placeholder="adicione uma nova tarefa :)"> 
        <button class="form-element" @click="add">+</button>  
    </div>
</template>

<script>
export default {
    data(){
        return {
            name:''
        }
    },
    methods: {
        add() {  //função adicionar
            this.$emit('taskAdded', {name: this.name}) //emite um evento 
            this.name = '' //limpa o valor do campo 
        }
    }

}
</script>

<style>

.form-element {
    outline: none;
    font-size: 2rem;
    border: 1px solid #ffffff;
    padding: 5px 10px 8px;
    color: #ffffff;
}
input.form-element {
    width:500px;
    background: #fff2;
    border-top-left-radius: 8px;
    border-bottom-left-radius: 8px;
}

button.form-element {
    border-left: none;
    background-color: #2196f3;
    border-top-right-radius: 8px;
    border-bottom-left-radius: 8px;
}


</style>