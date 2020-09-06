<template>
  <div class="container flex flex-col">
    <div>{{ game.name }}</div>
    <div>{{ game.involved_companies[0].company.name }}</div>
    <img :src="game.cover.url.replace('t_thumb', 't_cover_big')" alt="cover">
    <p>{{ game.summary }}</p>
    <div>{{ game.platforms[0].name }}</div>
    <div>{{ game.first_release_date }}</div>
    <div>{{ game.websites[0].url }}</div>
    <div>{{ game.total_rating }}</div>
    <div>{{ game.screenshots }}</div>
    <img
      v-for="(screenshot, index) in game.screenshots"
      :key="index"
      :src="screenshot.url.replace('t_thumb', 't_cover_big')"
      alt="screenshot"
    >
  </div>
</template>

<script>
export default {
  async asyncData ({ $axios, params }) {
    const { data } = await $axios.get(`/igdb/games/${params.id}?fields=name,involved_companies.company.name,cover.url,summary,platforms.name,first_release_date,websites.url,total_rating,screenshots.url,screenshots.height,screenshots.width&expand=involved_companies&platforms`)
    return { game: data[0] }
  }
}
</script>
