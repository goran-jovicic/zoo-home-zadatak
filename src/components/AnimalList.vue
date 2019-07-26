<template>
    <div>
        <form @submit.prevent="addAnimal()">
          <div>
            <label for="vrsta">Vrsta zivotinje : </label>
            <input id="vrsta" v-model="newAnimal.vrsta" type="text" />
          </div>
          <div>
            <label for="ime">Ime zivotinje : </label>
            <input id="ime" type="text" v-model="newAnimal.ime" />
          </div>
          <div>
            <label for="datum_rodjenja">Datum rodjenja zivotinje : </label>
            <input id="datum_rodjenja" v-model="newAnimal.datum_rodjenja" type="text" />
          </div>
          <div>
            <select v-model="newAnimal.sector">
              <option v-for="(sector,index) in sectors" :key="index">
                {{ sector }}
              </option>
            </select>
          </div>
          <button type="submit">Dodaj zivotinju</button>
        </form>
      <ul>
        <li v-for="(animal,index) in animals" :key="index">
          Vrsta zivotinje : {{ animal.vrsta }}
          <br>
          Ime zivotinje : {{ animal.ime }}
          <br>
          Datum rodjenja zivotinje : {{ animal.datum_rodjenja ? animal.datum_rodjenja : 'Nepoznat' }}
          <br>
          Sektor zivotinje : {{ animal.sectors }}
          <br>
          <button @click="removeAnimal(index)">Remove Animal</button>
          <br>
          <button @click="moveToTop(index)">Move to top</button>
        </li>
      </ul>
      <ul>
        <li v-for="(sector,index) in sectors" :key="index">
          {{ sector }}
        <button @click="showAnimalsSector(sector)">Vidi listu zivotinja</button>
        </li>
      </ul>
    </div>
</template>

<script>
export default {
  data () {
    return {
      newAnimal : this.getDefault(),

      animals : [
        { vrsta : 'Bigl', ime : 'Boni', datum_rodjenja : '2009' , sectors: 'Pas' },
        { vrsta : 'Vrana', ime : 'Gavro', datum_rodjenja : '2016', sectors: 'Ptica' },
        { vrsta : 'Bubasvaba', ime : 'Komro', datum_rodjenja : '2019', sectors: 'Insekt' }
      ],

      sectors : [
        'Pas', 'Ptica', 'Insekt'
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
    },

    addAnimal() {
      this.animals.push({...this.newAnimal})
      this.newAnimal = this.getDefault()
    },

    getDefault() {
      return {
        vrsta: '',
        ime: '',
        datum_rodjenja: '',
        sectors : ''
      }
    },

    showAnimalsSector(sector) {
      let sectorAnimals = this.animals.filter(animal => animal.sectors === sector).map(animal=>animal.ime)

      window.alert(sectorAnimals.join(', '))
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
ispod tabele životinja dodati tabelu sektora. Prikazati ime svakog sektora i button `Vidi listu životinja`.
Klik na button `Vidi listu životinja` treba da u alert prozoru prikaže listu životinja u tom sektoru
