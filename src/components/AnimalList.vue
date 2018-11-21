<template>
  <div class="container">
    <table class="table">
      <thead class="thead-dark">
        <tr>
          <th>Index</th>
          <th>Species</th>
          <th>Name</th>
          <th>Birth</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="(animal,index) in animals" :key="index">
          <th>{{ index + 1 }}</th>
          <td>{{ animal.species }}</td>
          <td>{{ animal.name }}</td>
          <td>{{ animal.birth != "" ? animal.birth : "Unknown" }}</td>
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
  }
}
</script>

<style lang="css">
</style>
