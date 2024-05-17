<template>
    <div class="book-form">
      <h2>Add New Book</h2>
      <form @submit.prevent="submitForm">
        <div>
          <label for="code">Book Code:</label>
          <input type="text" id="code" v-model="code" required />
        </div>
        <div>
          <label for="name">Book Name:</label>
          <input type="text" id="name" v-model="name" required />
        </div>
        <div>
          <label for="duration">Borrow Duration (days):</label>
          <input type="number" id="duration" v-model.number="duration" required />
        </div>
        <button type="submit">Add Book</button>
      </form>
    </div>
  </template>
  
  <script>
  import { ref } from 'vue';
  
  export default {
    name: 'BookForm',
    emits: ['add-book'],
    setup(props, { emit }) {
      const code = ref('');
      const name = ref('');
      const duration = ref('');
  
      const submitForm = () => {
        if (code.value.trim() && name.value.trim() && duration.value > 0) {
          const book = {
            code: code.value,
            name: name.value,
            duration: duration.value,
          };
  
          emit('add-book', book);
  
          // Reset form fields
          code.value = '';
          name.value = '';
          duration.value = '';
        } else {
          alert('Please fill in all fields correctly.');
        }
      };
  
      return {
        code,
        name,
        duration,
        submitForm,
      };
    },
  };
  </script>
  
  <style scoped>
  .book-form {
    margin-bottom: 20px;
  }
  
  .book-form form {
    display: flex;
    flex-direction: column;
    gap: 10px;
  }
  
  .book-form label {
    font-weight: bold;
  }
  
  .book-form input {
    padding: 8px;
    width: 200px;
  }
  
  .book-form button {
    padding: 8px;
    background-color: #42b983;
    color: white;
    border: none;
    cursor: pointer;
    border-radius: 5px;
  }
  
  .book-form button:hover {
    background-color: #38a169;
  }
  </style>
  