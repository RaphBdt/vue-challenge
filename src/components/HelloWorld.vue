<script>
export default {
  data() {
    return {
      firstname: 'Jean',
      age: 30,
      year: 2022,
      buttonVisible: false,
      family: [
        {
          firstname: "Jojo",
          lastname: "Bernard",
          age: "25"
        },
        {
          firstname: "Marie",
          lastname: "Blachère",
          age: "29"
        },
        {
          firstname: "Jean",
          lastname: "Bernard",
          age: "20"
        },
        {
          firstname: "Paul",
          lastname: "Pogba",
          age: 17
        },
      ]
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
    <div id="family">
      <p v-for="person in family" :key="person.lastname">{{person.firstname}}</p>
    </div>
    <button v-if="buttonVisible" id="crazy-button" @click="changeFirstname">
      Changement de prénom
    </button>
  </div>
</template>

<style scoped>

</style>
