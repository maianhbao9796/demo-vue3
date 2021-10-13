<template>
  <form @submit="addItem">
      <input type="text"  placeholder="Nhập việc mới..." v-model="title">
      <input type="submit" value="Thêm" class="add-btn">
  </form>
</template>

<script>
import { ref } from 'vue'
import { v4 as uuidv4 } from 'uuid'

export default {
    name: 'Addtodo',
    setup(props, context) {
        const title = ref('')
        const addItem = event => {
            event.preventDefault()

            const newItem = {
                id: uuidv4(),
                title: title.value,
                completed: false
            }

            context.emit('add-todo',newItem)

            title.value = ''
        }
        
        return {
            title,
            addItem
        }
    }
}
</script>

<style scoped>
form {
    display: flex;
    padding: 5px;
}

input[type='text'] {
    flex: 10;
    padding: 10px;
    outline: none;
    font-size: 16px;
}

input[type='submit'] {
    flex: 2;
    margin-left: 100px;
    margin-right: 5px;

}

</style>