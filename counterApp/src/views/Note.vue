<template >
    <main>
         <div v-if="showModal" class="overlay">
            <div class="modal">
                <textarea v-model.trim="newNote" name="note" id="note" cols="30" rows="10"></textarea>
               <p v-if="errorMessage">{{errorMessage}}</p>
                <button @click="addNote">Add Note</button>
              
                <button @click="showModal = false" class="close">Close</button>
            </div>
        </div> 
        <div class="container">
            <header>
                <h1>Note  </h1>
                <button @click="showModal = true">+</button>
            </header>
            <div class="card-container">
                <div v-for="note in notes" :key="note.id" class="card" :style="{backgroundColor: note.backgroundColor}">
                    <p class="main-text">
                        {{ note.text }}
                    </p>
                    <p class="date">
                        {{ note.date.toLocaleDateString("en-US") }}
                    </p>
                </div>
            </div>
        </div>
    </main>
</template>
<script setup>
import {ref} from "vue"
const showModal = ref(false)

const newNote = ref("")
const errorMessage = ref("") 
const notes = ref([])

function getRandomColor() {
  return "hsl(" + Math.random() * 360 + ", 100%, 75%)";
;
}

const addNote = () =>{
    if(newNote.value.length < 10){
        return errorMessage.value = "Note need to be 10 character or more"
    }
    notes.value.push({
        id: Math.floor(Math.random() * 1000000),
        text: newNote.value,
        date: new Date(),
        backgroundColor: getRandomColor()
    });
    showModal.value = false;
    newNote.value = "";
    errorMessage.value = "";
}
</script>
<style scoped>
main{
    height: 100vh;
    width: 100vw;
}
    
.container{
    max-width: 1000px;
    padding: 10px;
    margin: 0 auto;
}
header{
    display: flex;
    justify-content: space-between;
    align-items: center;
}
h1{
    font-weight: bold;
    margin-bottom: 25px;
    font-size: 75px;
}
header button{
    background-image: linear-gradient(to right, rgb(226, 91, 91), rgb(245, 245, 65));
    border: none;
    border-radius: 100%;
    padding: 10px;
    width: 50px;
    height: 50px;
    cursor: pointer;
    color: white;
    font-size: 20px;      
}
.card{
    width: 225px;
    height: 225px;
    border: none;
    border-radius: 15px;
    background-color: rgb(245, 245, 65);
    padding: 10px;
    display: flex;
    flex-direction: column;
    justify-content: space-between;
    margin-right: 20px;
    margin-bottom: 20px;
}
.date{
    font-size: 12.5px;
    font-weight: bold;
}
.card-container{
    display: flex;
    flex-wrap: wrap;
}
.overlay{
    position: absolute;
    width: 100%;
    height: 100%;
    background-color: rgba(0, 0, 0, 0.77);
    z-index: 10;
    display: flex;
    align-items: center;
    justify-content: center;
}
.modal{
    width: 750px;
    background-color: white;
    border-radius: 10px;
    padding: 30px;
    position: relative;
    display: flex;
    flex-direction: column;

}
.modal button{
    padding: 10px 20px;
    font-size: 20px;
    width: 100%;
    background-color: rgb(80, 8, 122);
    border: none;
    color: white;
    cursor: pointer;
    margin-top: 15px;
}
.modal .close {
    background-color: red;
    margin-top: 7px;
}
.modal p{
    color: red;
}
</style>