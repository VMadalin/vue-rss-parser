# vue-rss-parser
A simple component to embed RSS parsed feeds with Vuejs

## Install

```bash
npm i vue-rss-parser
```

## Usage
Import VueRssParser in your component

```js
import VueRssParser from "vue-rss-parser";
...
export default {
  name: "Demo",
  components: {
    VueRssParser
  },
  data() {
    return {
      feedUrl: "https://rss.app/feeds/hmsyAr3PyniBpmOd.xml",
      name: "",
      limit: 5,
    };
  },
};
```

Then use it in your template

```HTML
<template>
 <VueRssParser :feedUrl="feedUrl" :name="name" :limit="limit"/>
</template>
```

## Props


| name    | type   | default | description                       |
| ------- | ------ | ------- | --------------------------------- |
| feedUrl | String |         | RSS Feed URL                      |
| limit   | Number | 5       | Number of items to render         |
| Name    | String |         | Pass a name to replace feed title |

## Note

Due to CORS policy some RSS feeds can't be loaded in the browser.
You can load RSS feeds from your own server or use [RSS.app](https://rss.app).


## License

MIT
