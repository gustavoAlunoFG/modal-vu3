<template>
    <button class="btn btn-primary"
    @click="() => emit('login')">Modal</button>
</template>

<script>
export default {
  setup (_, { emit }) {
    return { emit }
  }
}
</script>
