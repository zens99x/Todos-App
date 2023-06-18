<template>
  <form @submit="addItem">
    <input type="text" placeholder="Viec moi...." v-model="title" />
    <input type="submit" value="add" class="add-btn" />
  </form>
</template>

<script>
import { ref } from 'vue'
// import { v4 as uuidv4 } from 'uuid'
export default {
  name: 'AddTodo',
  setup(props, context) {
    const title = ref('')

    const addItem = event => {
      event.preventDefault()
      const newItem = {
        // id: uuidv4(),
        title: title.value,
        conpleted: false
      }
      context.emit('add-todo', newItem)
      title.value = ''
    }
    return {
      title,
      addItem
    }
  }
}
</script>

<style scope>
form {
  display: flex;
}
input[type='text'] {
  flex: 10;
  padding: 5px;
}
input[type='submit'] {
  flex: 2;
}
</style>
