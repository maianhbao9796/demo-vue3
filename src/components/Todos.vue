<template>
    <div>
        ToDo
        <Addtodo 
            @add-todo="addTodo"
        />
        <TodoItem 
            v-for="todo in todos" 
            :key="todo.id" 
            :todoProps="todo"
            @item-completed="markCompleted"
            @delete-item="deleteTodo"
        />
    </div>
</template>

<script>

import { ref } from 'vue'
import TodoItem from './TodoItem'
import Addtodo from './Addtodo'
import { v4 as uuidv4 } from 'uuid'

export default {
    name: 'Todos',
    components: { TodoItem, Addtodo },
    
    setup() {
        const todos = ref([
            {
                id: uuidv4(),
                title: 'Việc 1',
                completed: false 
            },
            {
                id: uuidv4(),
                title: 'Việc 2',
                completed: false
            },
             {
                id: uuidv4(),
                title: 'Việc 3',
                completed: false
            },

        ])
        
        const markCompleted = id => {
            todos.value = todos.value.map(
                todo => {
                    if(todo.id == id) todo.completed = !todo.completed
                    return todo
                }
            )
        }

        const deleteTodo = id => {
            todos.value = todos.value.filter(
                todo => todo.id != id
            )
        }

        const addTodo = newTodo => {
            todos.value.push(newTodo)
        }

        return {
            todos,
            markCompleted,
            deleteTodo,
            addTodo
        }
    }
}
</script>

<style>

</style>