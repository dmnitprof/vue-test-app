<template>
  <form @submit.prevent>
    <h4>Создание поста</h4>
    <span
        :style="!post.title ? 'color: red': ''"
        v-if="!post.title">
      {{error.title}}
    </span>
    <d-input
        v-focus
        v-model="post.title"
        class="input"
        type="text"
        placeholder="название"/>

    <span
        :style="!post.body ? 'color: red': ''"
        v-if="!post.body">
      {{error.body}}
    </span>
    <d-input
        v-model="post.body"
        class="input"
        type="text"
        placeholder="описание"/>
    <d-button
        style="margin-top: 1rem"
        @click="createPost"
    >
      Создать
    </d-button>
  </form>
</template>

<script>
export default {
  data() {
    return {
      post: {
        title: '',
        body: ''
      },
      error: {
        title: '',
        body: ''
      }

    }
  },
  methods: {
    createPost() {
      if(this.post.title && this.post.body){
        this.post.id = Date.now()
        this.$emit('create', this.post)
        this.post = {
          title: '',
          body: ''
        }
      }else {
        this.error.title = 'Заполните назнание'
        this.error.body = 'Заполните описание'
      }
    }
  }
}

</script>

<style scoped>

form {
  display: flex;
  flex-direction: column;
}
</style>