<template>
  <v-app>
    <v-toolbar app>
      <v-toolbar-title class="headline">
        <span>Give me News</span>
      </v-toolbar-title>
    </v-toolbar>

    <v-content>
      <form-select @sourceIsSelected="getNews" />
      <article-results :articles="articles" />
    </v-content>
  </v-app>
</template>

<script>
import FormSelect from "./components/FormSelect";
import ArticleResults from "./components/ArticleResults";

export default {
  name: "App",
  components: {
    FormSelect,
    ArticleResults
  },
  data() {
    return {
      articles: []
    };
  },
  methods: {
    getNews: function(data) {
      let articles = data.articles.map((item, idx) => {
        var o = Object.assign({}, item);
        o.id = idx;
        return o;
      });
      this.articles = articles;
    }
  }
};
</script>
