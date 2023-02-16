<script>
export default {
  data() {
    return {
      firstname: "Jean",
      age: 30,
      year: 2022,
    }
  },
  mounted() {
    setInterval(() => {
      this.age++;
      this.year++;
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
      <p>En {{ year }}, {{ firstname }} aura {{ age }} ans</p>
    </div>
    <button id="crazy-button">
    </button>
  </div>
</template>

<style scoped>

</style>
