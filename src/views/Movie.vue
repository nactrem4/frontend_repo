<template>
  <h1>Welcome to Movies</h1>
  <div class="container-fluid">
    <div class="row row-cols-1 row-cols-md-4 g-4">
      <div v-for="thing in things" :key="thing.id" class="col">
        <div class="card h-100">
          <ing src="../asserts/moon.png" class="card-img-top" alt="thing.filmName + thing.filmDescription"> </ing>
          <div class="card-body">
            <h5 class="card-title">{{ thing.filmName }} {{ thing.filmDescription }} {{thing.filmGenre}}</h5>
            <p class="card-text">
              {{ thing.filmDescription }} {{ thing.filmName }} {{thing.filmGenre}}
            </p>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  // eslint-disable-next-line vue/multi-word-component-names
  name: 'Things',
  data () {
    return {
      things: []
    }
  },
  mounted () {
    const endpoint = process.env.VUE_APP_BACKEND_BASE_URL + '/api/v1/things'
    const requestOptions = {
      method: 'GET',
      redirect: 'follow'
    }
    fetch(endpoint, requestOptions)
      .then(response => response.json())
      .then(result => result.forEach(thing => {
        this.things.push(thing)
      }))
      .catch(error => console.log('error', error))
  }
}
</script>

<style scoped>
</style>
