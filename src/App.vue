<template>
  <center>
    <div id="app">
      <h2 class="app-heading">
        Search and Explore Wikipedia Articles
      </h2>
      <p class="app-body">
        The product is a small web application built using Vue.js and integrated
        with the Wikimedia Codex design system. It allows users to search for
        articles on Wikipedia by entering a title in the search bar. Upon
        searching, the application fetches information about the article from
        the Wikimedia API and displays the title and a short extract of the
        article in a visually appealing manner using Codex components and styles.
        Users can interact with the application to quickly access and read
        Wikipedia articles within a familiar and consistent design environment
        provided by the Wikimedia Codex design system.
      </p>
      <SearchBar @search="fetchArticle" />
      <ArticleDisplay v-if="article" :article="article" />
    </div>
  </center>
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
  font-family: var(--mw-ui-font-family-base);
  color: var(--mw-ui-color-text);
}

.app-heading {
  margin-top: 5vh;
  font-size: 24px;
  font-weight: bold;
  color: #333;
}

.app-body {
  width: 70vw;
  font-size: 16px;
  line-height: 1.6;
  color: #666;
}
</style>
