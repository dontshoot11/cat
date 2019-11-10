<template lang="pug">
div.app
    todoinput(@addTodo="addTodo")
    todolist(:todos="todos" @removeItem = "removeItem" @setPrice="setPrice")
    .counter Гуляем на
     .number {{totalPrice}} Р
     button.clear-button(@click = "clear") очистить список
     
    
    
</template>

<script>


    import todoinput from './todoinput'
    import todolist from './todolist'
    export default {
    components: {
        todoinput,
        todolist
    },
    data(){return{
        todos: [],
        totalPrice: 0,
        budget: 0
    }},
    methods:{
    addTodo(todo){this.todos.push(todo); 
        let tds = JSON.stringify(this.todos); 
            localStorage.setItem("tds", tds)},

    removeItem(id){this.todos = this.todos.filter(item=> item.id !== id); 
        let tds = JSON.stringify(this.todos);
            localStorage.setItem("tds", tds)},

    setPrice(item){this.todos = this.todos.map(todo =>(todo.id === item.id ? item: todo));
         let tds = JSON.stringify(this.todos); 
            localStorage.setItem("tds", tds);},
    
    

    calculateTotalPrice(){if(this.todos){
        
        
        let a =0; for(let i =0; i<this.todos.length; i++){a+=parseInt(this.todos[i].price)} this.totalPrice = a}},


    clear(){this.todos = [];  
            localStorage.clear()}
    },

    


    updated(){this.calculateTotalPrice()},

    created(){let tds = JSON.parse(localStorage.getItem("tds")); if(tds){this.todos = tds}
    this.calculateTotalPrice()
     },
    
    
    
    
    
    
    
    
    
    
    
    }
    
</script>

<style lang="scss" scoped>
.app {display: flex; flex-direction: column; min-height: 100vh}

 .counter{text-align: right; width: 100%;
 margin-top: 20px; margin-top: auto; margin-bottom: 100px; display: flex; justify-content: space-between;}

 .number {font-weight: bold; font-size: 48px}

 .clear-button {cursor: pointer; background: inherit; border: none; color: inherit;
 &:focus{border:none; outline: none}
 }





</style>