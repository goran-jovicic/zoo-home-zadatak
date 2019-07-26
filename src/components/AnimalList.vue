<template>
    <div>
      <ul>
        <li v-for="(animal,index) in animals" :key="index">
          Vrsta zivotinje : {{ animal.vrsta }}
          <br>
          Ime zivotinje : {{ animal.ime }}
          <br>
          Datum rodjenja zivotinje : {{ animal.datum_rodjenja ? animal.datum_rodjenja : 'Nepoznat' }}
          <br>
          <button @click="removeAnimal(index)">Remove Animal</button>
          <br>
          <button @click="moveToTop(index)">Move to top</button>
        </li>
      </ul>
    </div>
</template>

<script>
export default {
  data () {
    return {
      animals : [
        { vrsta : 'Pas', ime : 'Boni', datum_rodjenja : '2009' },
        { vrsta : 'Ptica', ime : 'Gavro', datum_rodjenja : '2016' },
        { vrsta : 'Insekt', ime : 'Komro', datum_rodjenja : '2019' }
      ]
    }
  },

  methods : {
    removeAnimal(index) {
      this.animals.splice(index,1)
    },

    moveToTop(index) {
      let animalCopy = this.animals[index]
      this.animals.splice(index,1)
      this.animals.unshift(animalCopy)
    }
  }
}
</script>

<style>
  table { 
    border-style: solid;
    border-width: 0.2rem;
  }
  th, td {
    border-style: solid;
    border-width: 0.1rem;
    margin: 0.5rem;
    padding: 0.5rem;
  }
  li {
    list-style: none;
    margin:1rem;
  }
</style>
// Za svaku životinju u tabeli dodati button `Move to top` koja treba da poziva funkciju koja će prebacivati datu životinju na početak niza.
// Commit-ovati urađeno
