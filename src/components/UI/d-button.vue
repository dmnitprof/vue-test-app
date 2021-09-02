<template>
<button  class="btn">
<slot></slot>
</button>
</template>

<script>
export default {
name: 'd-button'
}
</script>

<style scoped>

.btn {
  align-self: flex-end;
  padding: .5rem 1rem;
  background: none;
  border: 1px solid cadetblue;
  color: cadetblue;
}
</style>