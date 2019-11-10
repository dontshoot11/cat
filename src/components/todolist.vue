<template lang="pug">
    .todo-list
        .content
            ul.list
                li.item(v-for = "item in todos" )
                    todoListItem(:item = "item" @removeItem = "removeItem" @setPrice = 'setPrice')
                    
                               

  
</template>



<script>
import todoListItem from "./todolistitem"
export default {
    props: {todos:{}},
    components: {todoListItem},

    methods: {removeItem(id){this.$emit('removeItem', id)},
    setPrice(item){this.$emit('setPrice', item)}
 
}}
</script>