<script setup lang="ts">
import HelloWorld from './components/HelloWorld.vue'
</script>

<script lang="ts">
export default {
  mounted () {
    document.body.classList.add('bg-black')
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
</style>