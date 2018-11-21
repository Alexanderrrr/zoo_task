<template>
  <div class="container">
    <h3>Create Animal</h3>

    <form @submit.prevent='addAnimal()'>
      <div class="form-group">
        <label>Enter species</label>
        <input v-model="newAnimal.species" class="form-control form-control-sm" placeholder="species" required>
      </div>
      <div class="form-group">
        <label>Enter name of animal</label>
        <input v-model="newAnimal.name" class="form-control form-control-sm" placeholder="name" required>
      </div>
      <div class="form-group">
        <label>Enter day of birth</label>
        <input v-model="newAnimal.birth" class="form-control form-control-sm" placeholder="birth">
      </div>
      <div class="form-group" id="select">
        <p>please select where this animal belongs</p>
        <select v-model="newAnimal.sector" class="form-control form-control-sm" required>
          <optgroup label="select surface">
            <option v-for="(sector,index) in sectors" :key='index' v-bind:value="sector">{{ sector.name }}</option>
          </optgroup>
        </select>

      </div>
      <button type="submit" class="btn btn-default">Add Animal</button>
    </form>
  <hr>
    <table class="table">
      <thead class="thead-dark">
        <tr>
          <th>Index</th>
          <th>Species</th>
          <th>Name</th>
          <th>Birth</th>
          <th>Sector</th>
          <th></th>
          <th></th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="(animal,index) in animals" :key="index">
          <th>{{ index + 1 }}</th>
          <td>{{ animal.species }}</td>
          <td>{{ animal.name }}</td>
          <td>{{ animal.birth === '' ? "Unknown" : animal.birth }}</td>
          <td>{{ animal.sector.surface === '' ? 'not selected' : animal.sector.surface }}</td>
          <th>
            <button @click="moveAnimalToTop(animal)" class="btn btn-success">Move to top</button>
          </th>
          <th>
            <button @click="removeAnimal(animal)" class="btn btn-danger">Remove</button>
          </th>
        </tr>
      </tbody>
    </table>

  </div>

</template>

<script>
const sectors = [
  {name: 'Water-animals', surface: 'Water'},
  {name: 'Predators', surface: 'Cage'},
  {name: 'Ape', surface: 'Cage'}
];
export default {
  data(){
    return {
      newAnimal: {
        birth: "",
      },

      sectors: sectors,

      animals: [
        {species: "mammals", name: "dog", birth: "", sector: {name:'', surface: ''}},
        {species: "mammals", name: "horse", birth: "01.01.2000", sector: {name:'', surface: ''}},
        {species: "amphibians", name: "frog", birth: "", sector: {name:'', surface: ''}},
        {species: "reptiles", name: "snake", birth: "", sector: {name:'', surface: ''}},
        {species: "reptiles", name: "aligator", birth: "01.01.1800", sector: {name:'Water-animals', surface: 'water'}},
      ],
    };
  },

  methods: {
    removeAnimal(animal){
      let index = this.animals.indexOf(animal);
      this.animals.splice(index,1);
    },

    moveAnimalToTop(animal){
      let index = this.animals.indexOf(animal);
      this.animals.splice(index,1);
      this.animals.unshift(animal);
    },

    addAnimal(){
      this.animals.push(this.newAnimal)
      this.newAnimal = {}
    }
  }
}

</script>

<style lang="css">
  form{
    width: 50%;
    margin: auto;
  }

  #select{
     border: 1px solid green;
  }
</style>
