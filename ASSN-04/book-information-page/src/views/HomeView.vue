<template>
  <div>
    <!-- Book list table -->
    <table>
      <thead>
        <tr>
          <th>ID</th>
          <th>Book name</th>
          <th>Author name</th>
          <th>Number of pages</th>
          <th>Status</th>
          <th>Operations</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="book in books" :key="book.id">
          <td>{{ book.id }}</td>
          <td>{{ book.name }}</td>
          <td>{{ book.author }}</td>
          <td>{{ book.pages }}</td>
          <td>{{ book.status }}</td>
          <td>
            <button @click="editBook(book)">Edit</button>
            <button @click="deleteBook(book)">Delete</button>
          </td>
        </tr>
      </tbody>
    </table>
    
    <!-- Book form -->
    <form @submit.prevent="submitForm">
      <label for="book-name">Book name:</label>
      <input id="book-name" type="text" v-model="form.name" required>
      
      <label for="author-name">Author name:</label>
      <input id="author-name" type="text" v-model="form.author" required>
      
      <label for="pages">Number of pages:</label>
      <input id="pages" type="number" v-model="form.pages" required>
      
      <template v-if="isUpdating">
        <label for="status">Status:</label>
        <select id="status" v-model="form.status">
          <option value="issued">Issued</option>
          <option value="available">Available</option>
        </select>
        <button>Update Book</button>
      </template>
      
      <template v-else>
        <button>Add Book</button>
      </template>
    </form>
  </div>
</template>

<script>
export default {
  data() {
    return {
      books: [
        { id: 1, name: 'The Great Gatsby', author: 'F. Scott Fitzgerald', pages: 180, status: 'issued' },
        { id: 2, name: 'To Kill a Mockingbird', author: 'Harper Lee', pages: 281, status: 'available' },
        { id: 3, name: '1984', author: 'George Orwell', pages: 328, status: 'available' }
      ],
      form: {
        name: '',
        author: '',
        pages: '',
        status: ''
      },
      selectedBook: null
    }
  },
  computed: {
    isUpdating() {
      return !!this.selectedBook
    }
  },
  methods: {
    editBook(book) {
      this.selectedBook = book
      this.form.name = book.name
      this.form.author = book.author
      this.form.pages = book.pages
      this.form.status = book.status
    },
    deleteBook(book) {
      const index = this.books.indexOf(book)
      this.books.splice(index, 1)
    },
    submitForm() {
      if (this.isUpdating) {
        const index = this.books.indexOf(this.selectedBook)
        this.books[index] = { ...this.form, id: this.selectedBook.id }
        this.selectedBook = null
      } else {
        const newId = this.books.length + 1
        this.books.push({ ...this.form, id: newId })
      }
      this.form.name = ''
      this.form.author = ''
      this.form.pages = ''
      this.form.status = ''
    }
  }
}
</script>

<style>
  table {
    border-collapse: collapse;
    margin-bottom: 20px;
  }
  th, td {
    border: 1px solid black;
    padding: 5px;
    text-align: left;
  }
  button {
    margin-right: 10px;
  }
</style>
