<template>
<!-- <div id="auth" class="ui container">
  <h1 class="ui header">Books</h1>
    <div class="ui clearing segment">
    <h3 class="ui center header">Book list</h3>
  </div>
  <div class="ui segment">
  <div class="ui inverted relaxed divided list">
    <div class="item">
      <div class="content" v-for="book in books">
        <label>Title</label>
        <a v-bind:href="book.url">{{ book.title}}</a>
        <label>Author</label>
        <p>{{ book.author }}</p>
      </div>
    </div>
  </div>
</div>
  <!-- <form class="ui form">
  <div class="two fields">  
  <div class="field">
    <label>Title</label>
    <input type="text" name="first-name" placeholder="Title" v-model="title">
  </div>
  <div class="field">
    <label>Author</label>
    <input type="email" name="last-name" placeholder="author" v-model="author">
  </div>
  </div>
  <button class="ui right floated button" type="submit">Submit</button>
 </form> 
</div> -->
</template>

<script>
export default {
  name: 'auth',
  data () {
    return {
      title: '',
      author: ''
    }
  }
}
</script>

