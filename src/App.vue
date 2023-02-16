<script setup lang="ts">
import HelloWorld from './components/HelloWorld.vue'
</script>

<script lang="ts">
export default {
  mounted () {
    document.body.classList.add('bg-black');
    document.body.classList.add('body-app');
  },
}
</script>

<template>
    <div>
      <HelloWorld />
    </div>
</template>

<style>
  .bg-black {
    background: #333333;
    color: #ffffff;
  }

  .body-app {
    display: flex;
    justify-content: center;
    align-items: center;
  }
</style>