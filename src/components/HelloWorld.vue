<script>
// import mapboxgl from "mapbox-gl";

export default {
  data() {
    return {
      //accessToken: 'pk.eyJ1IjoiZGV2cmFwaCIsImEiOiJjbGU3NG83cXowMXl3M25uemIxcHB6Zmd1In0.Z_ZkjqQE1l26ErpbKdVdxg',
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
      ],
      newMemberFirstname: '',
      newMemberLastname: '',
      newMemberAge: 25,
      newMemberAddress: '',
      newMemberPhoneNumber: '',
      newMemberGender: '',
    }
  },
  mounted() {
    setInterval(() => {
      this.age++;
      this.year++;
    }, 3000);

    /*mapboxgl.accessToken = this.accessToken;

    new mapboxgl.Map({
      container: "mapContainer",
      style: "mapbox://styles/mapbox/streets-v11",
      center: [103.811279, 1.345399],
      zoom: 12,
      maxBounds: [
        [103.6, 1.1704753],
        [104.1, 1.4754753],
      ],
    });*/
  },
  methods: {
    changeFirstname() {
      if (this.firstname === 'Patrick') {
        this.firstname = 'Jean';
      } else {
        this.firstname = 'Patrick';
      }
    },
    addAFamilyMember(newMemberFirstname, newMemberLastname, newMemberAge, newMemberAddress, newMemberPhoneNumber, newMemberGender) {
      this.family.push(
        {
          firstname: newMemberFirstname,
          lastname: newMemberLastname,
          age: newMemberAge,
          address: newMemberAddress,
          phoneNumber: newMemberPhoneNumber,
          gender: newMemberGender
        }
      )
    },
    deleteAFamilyMember(positionOfMemberToDelete) {
      this.family.splice(positionOfMemberToDelete, 1);
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
  },
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
      <div v-for="(person, i) in familyByAge" :key="person.lastname" class="family-member">
        <p>{{person.firstname}} {{person.lastname}} a {{person.age}} ans. Adresse : {{person.address}} - Téléphone : Adresse : {{person.phoneNumber}} - Genre : {{person.gender}}</p>
        <button @click="deleteAFamilyMember(i)">Supprimer</button>
      </div>
    </div>
    <button v-if="buttonVisible" id="crazy-button" @click="changeFirstname">
      Changement de prénom
    </button>
    <form>
      <div>
        <div>
          <input type="text" placeholder="Jojo" v-model="newMemberFirstname" />
          <input type="text" placeholder="Bernard" v-model="newMemberLastname" />
          <input type="number" min="10" v-model="newMemberAge" />
          <mapbox-address-autofill access-token="pk.eyJ1IjoiZGV2cmFwaCIsImEiOiJjbGU3NG83cXowMXl3M25uemIxcHB6Zmd1In0.Z_ZkjqQE1l26ErpbKdVdxg">
            <input type="text" name="address" autocomplete="shipping street-address" v-model="newMemberAddress" />
          </mapbox-address-autofill>
          <input type="tel" placeholder="0601020304" v-model="newMemberPhoneNumber" />
          <select v-model="newMemberGender">
            <option disabled value="">Choix</option>
            <option value="male">Homme</option>
            <option value="female">Femme</option>
          </select>
        </div>
        <button type="button" id="add-family-member" @click="addAFamilyMember(newMemberFirstname, newMemberLastname, newMemberAge, newMemberAddress, newMemberPhoneNumber, newMemberGender)">
          Ajouter un membre dans la famille
        </button>
      </div>
    </form>
    <!--<div id="mapContainer" class="basemap"></div>-->
  </div>
</template>

<style scoped>
  .family-member {
    display: flex;
    align-items: center;
  }

  #age {
    margin-bottom: 30px;
  }

  #family {
    margin-bottom: 15px;
  }

  form {
    margin-bottom: 20px;
  }

  #mapContainer {
    width: 500px;
    height: 500px;
  }

  .geocoder {
    width: 300px;
    height: 50px;
  }
</style>
