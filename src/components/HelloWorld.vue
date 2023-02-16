<script>
export default {
  data() {
    return {
      firstname: "Jean"
    }
  }
}
</script>

<template>
  <div>
    <div id="presentation">
      <p>Bonjour je m'appelle {{ firstname }}</p>
    </div>
    <div id="age">
      <p>En 2022, {{ firstname }} aura 30 ans</p>
    </div>
  </div>
</template>

<style scoped>

</style>
