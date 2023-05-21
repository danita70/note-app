<script setup>
import { ref } from 'vue';
const count = ref(0)

</script>

<template>
 <main>
  <div class="add">
    <h2>The current count is...</h2>

        <h1>{{count}}</h1>
        <div >
          <button @click="count--">-</button>
          <button @click="count++">+</button>
        </div>
        
 </div>
 </main>
</template>
<style scoped>
main{
  background-color: aliceblue;
  margin: 25px 25px;
  height: 50vh;
  width: 50vw;
  display: flex;
  align-content: center;
  justify-content: center;
}
.add{

  text-align: center;
}
h1{
 
}

button{
 width: 120px;
 padding: 16px 20px;
 margin-right: 25px;
   border: none;
   border-radius: 25px;
   color: white;
  background-image: linear-gradient(to right,  red, yellow);
}
</style>