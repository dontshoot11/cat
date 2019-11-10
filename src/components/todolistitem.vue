<template lang="pug">
    .todo-item
                       
                            
                                
                        .title {{item.name}} 
                        .price
                            label И стоит это удовольствие
                                .row
                                    input(type="number"  @keydown.enter = "setPrice" v-model = "item.price" ).number
                                    span.ruble  Р

                        .button
                            button(type="button" @click="removeItem").remove удоли
</template>






<style lang="scss" scoped>
.todo-item {display: grid; grid-template-columns: 1fr 1fr 0.3fr; align-items: center; text-align: left; margin: 20px 0px;  &:hover{.button{visibility: visible}} }
.button {visibility: hidden; display: flex; align-items: center}

.remove {cursor: pointer; background: inherit; border: none; color: inherit}

 label {display: flex; flex-direction: column}

 .title {font-weight: bold; font-size: 30px}

 .number {font-size: 30px; max-width: 30%}

 .ruble {font-size: 28px}

 @media (max-width: 560px) {
     .todo-item{max-width: 100%}
    
     .todo-item {display: grid; grid-template-rows: 1fr 1fr 0.3fr;
     grid-template-columns: 1fr ; max-width: 100vw; overflow: hidden;}
     .button {visibility: visible; display: flex; align-items: center; margin: 20px 0; max-width: 90vw;  justify-content: flex-end;}
 
     
    

     
 }




 





</style>

<script>


export default {
    data(){return{
        cost: ""
    }},
   
    props: {item: {},},
    methods: {
    removeItem(){this.$emit('removeItem', this.item.id)},



    setPrice(){
    const item = {...this.item};

    this.$emit("setPrice", item)
    
    
    },
   
    
    
    
    
    }
}

</script>