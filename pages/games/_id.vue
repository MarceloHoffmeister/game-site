<template>
  <div>Game detail page</div>
</template>

<script>
export default {
  async asyncData ({ $axios, params }) {
    const { data } = await $axios.get(`/igdb/games/${params.id}?fields=name,involved_companies.company.name,cover,summary,platforms.name,first_release_date,websites.url,total_rating,screenshots.url,screenshots.height,screenshots.width&expand=involved_companies&platforms`)
    return { game: data[0] }
  }
}
</script>
