<script>
export default {
  data() {
    return {
      firstname: 'Jean',
      age: 30,
      year: 2022,
      buttonVisible: false
    }
  },
  mounted() {
    setInterval(() => {
      this.age++;
      this.year++;
    }, 3000);
  },
  methods: {
    changeFirstname() {
      if (this.firstname === 'Patrick') {
        this.firstname = 'Jean';
      } else {
        this.firstname = 'Patrick';
      }
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
      <p>En {{ year }}, {{ firstname }} aura {{ age }} ans</p>
    </div>
    <button v-if="buttonVisible" id="crazy-button" @click="changeFirstname">
      Changement de prénom
    </button>
  </div>
</template>

<style scoped>

</style>
