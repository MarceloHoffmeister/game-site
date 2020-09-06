<template>
  <div class="container">
    <div class="game-container">
      <nuxt-link v-for="game in games" :key="game.id" :to="'/games/' + game.id" class="block mb-8">
        <img :src="game.cover.url.replace('t_thumb', 't_cover_big')" alt="cover" class="mx-auto">
        <div>{{ game.name }}</div>
        <div>{{ game.genres[0].name }}</div>
      </nuxt-link>
    </div>
  </div>
</template>

<script>

export default {
  async asyncData ({ $axios }) {
    const { data } = await $axios.get('/igdb/games?fields=name,popularity,genres.name,cover.url&order=popularity:desc&exapand=genres')
    return { games: data }
  }
}

</script>

<style>
/* Sample `apply` at-rules with Tailwind CSS
.container {
@apply min-h-screen flex justify-center items-center text-center mx-auto;
}
*/
.container {
  margin: 0 auto;
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
}

.title {
  font-family:
    'Quicksand',
    'Source Sans Pro',
    -apple-system,
    BlinkMacSystemFont,
    'Segoe UI',
    Roboto,
    'Helvetica Neue',
    Arial,
    sans-serif;
  display: block;
  font-weight: 300;
  font-size: 100px;
  color: #35495e;
  letter-spacing: 1px;
}

.subtitle {
  font-weight: 300;
  font-size: 42px;
  color: #526488;
  word-spacing: 5px;
  padding-bottom: 15px;
}

.links {
  padding-top: 15px;
}
</style>
