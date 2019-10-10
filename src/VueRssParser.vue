<template>
  <div class="vue-rss-parser">
    <Feed :feedUrl="feedUrl" :limit="limit"/>
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
    limit: Number
  }
};
</script>
