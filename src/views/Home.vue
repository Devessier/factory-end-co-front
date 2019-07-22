<template>
  <div class="home">
    <section class="container">
      <article
          v-for="({ title }, i) in articles"
          :key="i"
      >
        {{ title }}
      </article>
    </section>
  </div>
</template>

<script>


export default {
  name: 'home',
  data () {
    return {
      articles: []
    }
  },
  created () {
    fetch('http://localhost:8000/articles', {
      mode: 'cors'
    })
      .then(res => res.json())
      .then(articles => {
        this.articles = articles
      })
      .catch(console.error)
  }
}
</script>

<style>

  .container {
    display: flex;
    flex-direction: column;
  }

  .container article {
    
  }

</style>

