<script setup>
import { ref, reactive} from 'vue';

//let todo = reactive([]);
const state = reactive({todos: []})
let id = 0;

const handleSubmit = (data)=>{
    state.todos.push({
        value:data,
        id:id++})
    console.log(state.todos)
}

const handleDelete = (id)=>{
    state.todos = state.todos.filter(function (item){
        if (item.id !== id) {
            return true
        }
    })

    console.log(state.todos)
}

</script>

<template>
    <div class="search">
        <input v-model="inputText"/>
        <button @click="handleSubmit(inputText)">Submit</button>
    </div>
    <div class="todolist">
        TodoList
        <div>
            <ul>
                <li class="todo" v-for="item in state.todos" :key="item.id">{{item.value}} <button class="delete" @click="$event=> handleDelete(item.id)">delete</button> </li>
            </ul>
        </div>
    </div>
</template>

<style scoped>
.search{
    padding-top: 30px;
}

.todolist{
    margin-top: 10px;
    box-sizing: border-box;
    border: 1px solid black;
}

ul {
    padding: 5px;
}

.todo{
    display:flex;
    justify-content: space-between;
}

</style>