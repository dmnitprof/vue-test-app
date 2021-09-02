<template>
  <div class="app">
    <post-form

        @create="createPost"
    />
    <post-list
        :posts="posts"
    />
  </div>
</template>

<script>
import PostForm from './components/PostForm.vue'
import PostList from './components/PostList.vue'

export default {
  components: {
    PostForm,
    PostList
  },
  data() {
    return {
      posts: [
        {id: 1, title: 'Javascript', body: 'описание поста'},
        {id: 2, title: 'Javascript 2', body: 'описание поста 2'},
        {id: 3, title: 'Javascript 3', body: 'описание поста 3'}
      ],
    }
  },
  methods: {
    createPost(post) {
      this.posts.push(post)
    }
  }
}

</script>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

.app {
  padding: .5rem;
}
</style>