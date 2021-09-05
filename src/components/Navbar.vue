<template>
<div class="navbar">
<div @click="$router.push('/')">Vue 3 >> на главную</div>
  <div class="navbar__btns">
    <d-button @click="$router.push('/posts')">Посты</d-button>
    <d-button @click="$router.push('/about')" style="margin-left: 1rem">О Приложении</d-button>
    <d-button @click="$router.push('/store')" style="margin-left: 1rem">Store</d-button>
    <d-button @click="$router.push('/composition')" style="margin-left: 1rem">compositionApi</d-button>
  </div>

</div>
</template>

<script>
export default {
  name: "Navbar"
}
</script>

<style scoped>
.navbar {
  height: 50px;
  background: lightgray;
  box-shadow: 2px 2px 4px lightgray;
  display: flex;
  align-items: center;
  padding: 0 1rem;
}
.navbar__btns {
  margin-left: auto;
}
</style>