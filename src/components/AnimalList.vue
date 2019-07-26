<template>
    <div>
      <table>
        <tr>
          <th>Vrsta zivotinje</th>
          <th v-for="(animal,index) in animals" :key="index">{{ animal.vrsta }}</th>
        </tr>
        <tr>
          <td>Ime zivotinje</td>
          <td v-for="(animal,index) in animals" :key="index">{{ animal.ime }}</td>
        </tr>
        <tr>
          <td>Rodjenje zivotinje</td>
          <td v-for="(animal,index) in animals" :key="index">{{ animal.datum_rodjenja ? animal.datum_rodjenja : 'nepoznat' }}</td>
        </tr>
      </table>
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
</style>


// U komponentu postaviti niz objekata koji predstavlja niz od 5 proizvoljnih životinja. 
// Svaka životinja treba da ima:
// 	- vrstu
// 	- ime
// 	- datum rođenja
// `AnimalList` treba da prikaže sve životinje dodate u listu. Prikazati sva tri polja u tabeli.