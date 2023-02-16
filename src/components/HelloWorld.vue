<script>
export default {
  data() {
    return {
      firstname: "Jean",
      age: 30
    }
  },
  mounted() {
    setInterval(() => {
      this.age++
    }, 3000);
  }
}
</script>

<template>
  <div>
    <div id="presentation">
      <p>Bonjour je m'appelle {{ firstname }}</p>
    </div>
    <div id="age">
      <p>En 2022, {{ firstname }} aura {{ age }} ans</p>
    </div>
  </div>
</template>

<style scoped>

</style>
