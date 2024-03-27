<template>
  <div id="app" class="mw-ui-container">
    <SearchBar @search="fetchArticle" />
    <ArticleDisplay v-if="article" :article="article" />
  </div>
</template>

<script>
import SearchBar from "./components/SearchBar.vue";
import ArticleDisplay from "./components/ArticleDisplay.vue";

export default {
  name: "App",
  components: {
    SearchBar,
    ArticleDisplay,
  },
  data() {
    return {
      article: null,
    };
  },
  methods: {
    async fetchArticle(title) {
      try {
        const response = await fetch(
          `https://en.wikipedia.org/api/rest_v1/page/summary/${title}`
        );
        const data = await response.json();
        this.article = {
          title: data.title,
          extract: data.extract,
        };
      } catch (error) {
        console.error(error);
      }
    },
  },
};
</script>

<style scoped>
#app {
  /* Use Wikimedia's base font styles */
  @import url("https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.2.0/css/all.min.css");
  font-family: var(--mw-ui-font-family-base);
  color: var(--mw-ui-color-text);
}
</style>