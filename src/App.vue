<template lang="pug">
.container 
  
  todo
</template>

<script>
import todo from "./components/todo"


export default {
  name: 'app',
  components: {
    todo
  
  }
}
</script>

<style lang="scss">
body {
  font-family: 'Roboto', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: greenyellow;
  height: 100vh;
  padding: 0;
  margin: 0;
 
  background: url('./assets/cat.jpg');
}
ul {padding: 0;
margin: 0}
li{list-style: none}
input {background: #000; border:greenyellow 1px solid; color: greenyellow; outline:none; max-width: 100%;}
.container { margin: 0 auto; max-width: 50%; min-height: 100%; background: #000; }


input[type=number]::-webkit-inner-spin-button,
input[type=number]::-webkit-outer-spin-button {
    -webkit-appearance: none;
    -moz-appearance: none;
    appearance: none;
    margin: 0;
}

input[type=number]{
  -moz-appearance: textfield;
}

 @media (max-width: 768px) {
     .container {max-width: 80%}
     
 }

 @media (max-width: 560px) {
   
     .container {max-width: 90%}
    
    

     
 }


</style>
