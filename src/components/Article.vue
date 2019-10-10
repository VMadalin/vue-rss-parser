<template>
  <div class="article">
    <a :href="article.link" target="_blank">
      <div class="image">
        <img :src="getImageUrl(article['content:encoded'])" :alt="article.title" />
      </div>
      <div class="title">
        <h3>{{article.title}}</h3>
      </div>
    </a>
    <div class="footer">
      <span class="hostname">{{this.getHostname()}}</span>
      <span v-if="article.isoDate" class="middot">&bull;</span>
      <span class="datetime">{{this.getDateTime()}}</span>
    </div>
  </div>
</template>

<script>
const parseDate = tdate => {
  const systemDate = new Date(Date.parse(tdate));
  const userDate = new Date();

  const diff = Math.floor((userDate - systemDate) / 1000);
  if (diff < 59) {
    return diff + "s";
  }

  if (diff <= 3540) {
    return Math.round(diff / 60) + "m";
  }

  if (diff <= 86400) {
    return Math.round(diff / 3600) + "h";
  }

  if (diff < 604800) {
    return Math.round(diff / 86400) + "d";
  }

  return systemDate.toString().substring(4, 10);
};

export default {
  name: "Article",
  props: ["article"],
  methods: {
    getHostname() {
      try {
        const urlObj = new URL(this.article.link);
        return urlObj.hostname.replace("www.", "").replace("ww2.", "");
      } catch (e) {
        console.error(e.toString());
      }
    },
    getDateTime() {
      if (this.article.isoDate) {
        return parseDate(this.article.isoDate);
      }
    },
    getImageUrl(string) {
      const Regex = /<figure><img[^>]*src *= *['\"]?([^'\" >]+)['\"]?[^>]*><\/figure>/g;
      return Regex.exec(string)[1];
    }
  }
};
</script>

<style scoped>
h3 {
  margin: 0;
  padding: 0;
}

.article {
  position: relative;
  display: flex;
  flex-direction: column;
  min-width: 0;
  word-wrap: break-word;
  background-color: #fff;
  padding: 1.25rem;
  margin-bottom: 1rem;
}

.article .image {
  margin-bottom: 12px;
}

.article .image img {
  display: block;
  max-width: 100%;
}

.body .content {
  margin-top: 5px;
}
.footer {
  font-size: 13px;
  color: #777;
  display: flex;
  align-items: flex-end;
}
.middot {
  font-size: 12px;
  margin: 0 8px;
}
</style>
