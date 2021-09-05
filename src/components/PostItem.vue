<template>
  <div class="post">
    <div>
      <div>post-id: {{(post.id)}}</div>
      <div><strong>Название:</strong>{{ post.title }}</div>
      <div><strong>Описание:</strong>{{ post.body }}</div>
    </div>
    <div class="post__btns">
      <d-button
          @click="$router.push(`/posts/${post.id}`)"
      >Открыть</d-button>
      <d-button
          @click="$emit('remove', post)"
      >Удалить</d-button>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    post: {
      type: Object,
      required: true
    }
  }

}

</script>

<style scoped>

.post {
  padding: .5rem;
  border: 2px solid cadetblue;
  margin-top: .5rem;
  display: flex;
  align-items: center;
  justify-content: space-between;
}
.post__btns {
display: flex;
}

</style>