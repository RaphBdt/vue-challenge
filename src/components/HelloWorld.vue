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
          firstname: 'Jojo',
          lastname: 'Bernard',
          age: 25,
          address: '79 Place de la Gare, 73000 Chambéry',
          phoneNumber: '0612345678',
          gender: 'male'
        },
        {
          firstname: 'Marie',
          lastname: 'Blachère',
          age: 29,
          address: '14 Avenue du Rhône, 74000 Annecy',
          phoneNumber: '0601020304',
          gender: 'female'
        },
        {
          firstname: 'Jean',
          lastname: 'Bernard',
          age: 20,
          address: '1 Rue Claude Martin, 73000 Chambéry',
          phoneNumber: '0687654321',
          gender: 'male'
        },
        {
          firstname: 'Paul',
          lastname: 'Pogba',
          age: 17,
          address: '75 avenue des Champs Élysées, 75000 Paris',
          phoneNumber: '0600112233',
          gender: 'male'
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
  },
  computed: {
    familyByAge() {
      function compare( a, b ) {
        if ( a.age < b.age ){
          return -1;
        }
        if ( a.age > b.age ){
          return 1;
        }
        return 0;
      }

      return this.family.sort( compare );;
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
      <p v-for="person in familyByAge" :key="person.lastname">{{person.firstname}} {{person.lastname}} a {{person.age}} ans. Adresse : {{person.address}} - Téléphone : Adresse : {{person.phoneNumber}} - Genre : {{person.gender}}</p>
    </div>
    <button v-if="buttonVisible" id="crazy-button" @click="changeFirstname">
      Changement de prénom
    </button>
  </div>
</template>

<style scoped>

</style>
