<template>
  <div class="vue-rss-parser">
    <Feed :feedUrl="feedUrl" :name="name" :limit="limit"/>
  </div>
</template>

<script>
import Feed from "./components/Feed.vue";

export default {
  name: "VueRssParser",
  components: {
    Feed
  },
  props: {
    feedUrl: String,
    name: String,
    limit: Number
  }
};
</script>

<style scoped>
.vue-rss-parser {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  max-width: 600px;
  width: 100%;
  text-align: center;
}
</style>
