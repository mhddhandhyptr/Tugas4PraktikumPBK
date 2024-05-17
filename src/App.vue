<template>
  <div id="app">
    <h1>Book Library</h1>
    <BookForm @add-book="addBook" />
    <BookList :books="books" />
  </div>
</template>

<script>
import { ref } from 'vue';
import BookForm from './components/from.vue';
import BookList from './components/list.vue';

export default {
  name: 'App',
  components: {
    BookForm,
    BookList,
  },
  setup() {
    const books = ref([]);

    const addBook = (book) => {
      books.value.push(book);
    };

    return {
      books,
      addBook,
    };
  },
};
</script>

<style scoped>
#app {
  background: linear-gradient(to right, #74ebd5, #acb6e5);
  color: #333;
  padding: 20px;
  max-width: 800px;
  margin: 0 auto;
  box-shadow: 0 10px 20px rgba(0,0,0,0.19), 0 6px 6px rgba(0,0,0,0.23);
}

/* Style the h1 with a text shadow for depth */
h1 {
  color: #fff;
  text-shadow: 2px 2px 4px #000;
}

/* Improve the form input aesthetics */
.book-form input {
  border: 2px solid #74ebd5;
  box-shadow: inset 0 1px 3px rgba(0,0,0,0.12), 0 1px 2px rgba(0,0,0,0.24);
}

/* Style the button to be more eye-catching */
.book-form button {
  background-color: #8e44ad;
  border-radius: 20px;
  padding: 10px 15px;
  font-size: 16px;
  box-shadow: 0 2px 4px #333;
}

.book-form button:hover {
  background-color: #9b59b6;
}

/* Add more styling to the book list for better readability */
.book-list th, .book-list td {
  text-align: center;
  border: 2px solid #74ebd5;
}

.book-list tr:nth-child(even) {
  background-color: #e8f8f5;
}

.book-list tr:hover {
  background-color: #d1f2eb;
  transform: scale(1.02);
  transition: transform 0.2s ease-in-out;
}

/* Add a footer with some padding */
footer {
  padding: 20px;
  background-color: #2c3e50;
  color: white;
  text-align: center;
  margin-top: 40px;
}
</style>
