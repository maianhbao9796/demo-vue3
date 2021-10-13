<template>

  <p :class="['todo-item', todoProps.completed ? 'is-completed' : '']">
    <input 
      type="checkbox" 
      :checked="todoProps.completed" 
      @change="markItemCompleted"
    >
    <span class="todo-item__content">
      {{ todoProps.title }}
    </span>
    <button class="todo-item__del-btn" 
      @click="deleteItem">
      Delete
    </button>
  </p>
  
</template>

<script>

export default {
  name: 'TodoItem',
  props: ['todoProps'],
  setup (props, context) {
    const markItemCompleted = () => {
      context.emit('item-completed', props.todoProps.id)
    }

    const deleteItem = () => {
      context.emit('delete-item', props.todoProps.id)
    }

    return {
      markItemCompleted,
      deleteItem
    }
  }
}

</script>

<style>
.todo-item {
  margin: 0;
  background-color: #f4f4f4;
  padding: 10px;
  border-bottom: 1px solid #c7c7c7;
}

.todo-item__content {
  padding: 0 5px;
}

.todo-item__del-btn {
  background-color: red;
  color: #fff;
  padding: 3px 10px;
  border: none;
  float: right;
}

.is-completed {
  text-decoration: line-through;
}

</style>