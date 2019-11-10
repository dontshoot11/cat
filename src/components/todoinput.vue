<template lang="pug">
    .todo-input
        input(
            type="text",
            placeholder = "На что тратим?",
            autofocus
            v-model = "todo.name"
            @keydown.enter = "addTodo"
           
        )
    
</template>

<style lang="scss" scoped>
input {font-size: 36px; font-weight: bold; border: none; border-bottom: 2px solid greenyellow; margin-top: 25%;}
</style>

<script>
let id = 0;
export default {
    data(){return {
        todo: {id: 0,
        name: "",
        price: 0,
        }
    }







    },
    methods: {addTodo(){
        id++;
        this.todo.id = id;
        if (this.todo.name) {this.$emit('addTodo', {...this.todo});
        this.todo.name = "";
} else this.todo.name = "Без имени? Ну ладно"
        



    }}
}
</script>