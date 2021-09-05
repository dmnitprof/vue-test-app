<template>
  <input :value="modelValue" @input="updateInput" type="text" class="input">
</template>

<script>
export default {
  name: 'd-input',
  props: {
    modelValue: [String, Number]
  },
  methods: {
    updateInput(e) {
      this.$emit('update:modelValue', e.target.value)
    }
}
}
</script>

<style scoped>

.input {
  width: 100%;
  border: 1px solid cadetblue;
  padding: .5rem 1rem;
  margin-top: 1rem;
}
</style>