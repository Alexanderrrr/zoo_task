<template>
  <div class="container">
    <table class="table">
      <thead class="thead-dark">
        <tr>
          <th>Index</th>
          <th>Species</th>
          <th>Name</th>
          <th>Birth</th>
          <th></th>
          <th></th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="(animal,index) in animals" :key="index">
          <th>{{ index + 1 }}</th>
          <td>{{ animal.species }}</td>
          <td>{{ animal.name }}</td>
          <td>{{ animal.birth != "" ? animal.birth : "Unknown" }}</td>
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
export default {
  data(){
    return {
      animals: [
        {species: "mammals", name: "dog", birth: ""},
        {species: "mammals", name: "horse", birth: "01.01.2000"},
        {species: "amphibians", name: "frog", birth: ""},
        {species: "reptiles", name: "snake", birth: ""},
        {species: "reptiles", name: "aligator", birth: "01.01.1800"},
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
    }
  }
}
</script>

<style lang="css">
</style>
