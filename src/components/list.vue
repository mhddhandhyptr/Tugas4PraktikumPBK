<template>
    <div class="book-list">
      <h2>Book List</h2>
      <table>
        <thead>
          <tr>
            <th>Book Code</th>
            <th>Book Name</th>
            <th>Borrow Duration (days)</th>
          </tr>
        </thead>
        <tbody>
          <tr v-for="(book, index) in books" :key="index">
            <td>{{ book.code }}</td>
            <td>{{ book.name }}</td>
            <td>{{ book.duration }}</td>
          </tr>
        </tbody>
      </table>
    </div>
  </template>
  
  <script>
  export default {
    name: 'BookList',
    props: {
      books: {
        type: Array,
        required: true,
      },
    },
  };
  </script>
  
  <style scoped>
  .book-list {
    margin-top: 20px;
    font-family: Arial, sans-serif;
  }
  
  .book-list table {
    width: 100%;
    border-collapse: collapse;
  }
  
  .book-list th,
  .book-list td {
    border: 1px solid #ddd;
    padding: 8px;
  }
  
  .book-list th {
    background-color: #f4f4f4;
    text-align: left;
  }
  
  .book-list tr:nth-child(even) {
    background-color: #f9f9f9;
  }
  
  .book-list tr:hover {
    background-color: #f1f1f1;
  }
  </style>
  