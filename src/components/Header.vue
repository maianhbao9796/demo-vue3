<template>
  <header class="header">
      <h1>App I DO</h1>
  </header>
</template>

<script>
export default {
    name: 'Header',
    data() {
        return {
            a: 'Hello'
        }
    }
}
</script>

<style scoped>
    .header {
        background-color: #333;
        color: #fff;
        text-align: center;
        padding: 10px;
    }
</style>