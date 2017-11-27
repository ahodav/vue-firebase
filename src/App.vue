<template>
  <div id="app">
<div id="auth" class="ui container">
  <h1 class="ui header">Add book</h1>

  <form class="ui form" @submit.prevent="addBook">
  <div class="three fields">
    <div class="field">
      <label for="bookTitle">Book</label>
      <input type="text" id="bookTitle" placeholder="Book" v-model="newBook.title">
    </div>
    <div class="field">
      <label>Author</label>
      <input type="text" placeholder="Author" v-model="newBook.author">
    </div>
    <div class="field">
      <label>Url</label>
      <input type="text" placeholder="Url" v-model="newBook.url">
    </div>
  </div>
  <button class="fluid ui button">Add</button>
  </form>

<div class="ui clearing segment">
    <h3 class="ui center header">Book list</h3>
  </div>

  <div class="ui segment">

  <table class="ui compact celled table">
  <thead>
    <tr>
      <th>Book</th>
      <th>Author</th>
      <th>Delete</th>
    </tr>
  </thead>
  <tbody>
    <tr v-for="book in books" :key="book">
      <td><a v-bind:href="book.url">{{ book.title }}</a></td>
      <td>{{ book.author }}</td>
      <td>
        <span><i class="remove icon" @click="removeBook(book)"></i></span> 
      </td>
    </tr>
  </tbody>

</table>
   <router-view/>
  </div>
</div>
  </div>
</template>

<script>
import Firebase from 'firebase'

const config = {
  apiKey: 'AIzaSyDG6kkti3XFZ0hBN2mB_Rg-eJ5Cl8hewdg',
  authDomain: 'vue-firebase-eb506.firebaseapp.com',
  databaseURL: 'https://vue-firebase-eb506.firebaseio.com',
  projectId: 'vue-firebase-eb506',
  storageBucket: 'vue-firebase-eb506.appspot.com',
  messagingSenderId: '9493686591'
}

const app = Firebase.initializeApp(config)
const db = app.database()

const bookref = db.ref('books')

export default {
  name: 'app',
  firebase: {
    books: bookref
  },
  data () {
    return {
      newBook: {
        title: '',
        author: '',
        url: ''
      }
    }
  },
  methods: {
    addBook: function () {
      bookref.push(this.newBook)
      this.newBook.title = ''
      this.newBook.author = ''
      this.newBook.url = ''
    },
    removeBook: function (book) {
      bookref.child(book['.key']).remove()
    }
  }
}
</script>

<style>
#app {
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
