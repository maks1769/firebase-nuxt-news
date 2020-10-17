<template>
  <div class="main-content">
    <ul>
      <NewsItem v-for="item of news" :key="item.id" :item="item"/>
    </ul>

    <div class="add-news">
      <span>Предложить новость:</span>
      <input type="text" v-model="title" placeholder="Заголовок">
      <textarea v-model="content" placeholder="Краткое описание"></textarea>
      <button @click="addNewArticle">Добавить</button>
    </div>
  </div>
</template>

<script>
import NewsItem from "../components/pages/NewsItem";

export default {
  data() {
    return {
      title: '',
      content: '',
    }
  },

  components: {
    NewsItem
  },

  methods: {
    addNewArticle() {
      this.$fireStore.collection('news').doc().set({
        title: this.title,
        content: this.content,
      });

      this.title = '';
      this.content = '';
    }
  },

  async asyncData({$fireStore}) {

    const newsRef = $fireStore.collection('news');

    const news = await newsRef.get();

    const data = [];

    for (let item of news.docs) {
      data.push({
        id: item.id,
        ...item.data()
      })
    }

    return {
      news: data
    };
  }
}
</script>

<style>
  .main-content {
    display: flex;
    justify-content: space-between;
  }

  .add-news {
    display: flex;
    flex-direction: column;
    width: 500px;
  }

  .add-news > * {
    margin-bottom: 10px;
  }

  .add-news > input {
    height: 30px;
  }

  .add-news > textarea {
    height: 80px;
  }

  .add-news > button {
    width: 100px;
  }

  h2 {
    margin-bottom: 10px;
  }

  ul {
    max-width: 600px;
  }

  a {
    text-decoration: none;
    color: initial;
  }

  li {
    border: 1px solid black;
    padding: 10px;
    max-width: 500px;
    border-radius: 10px;
    margin-bottom: 10px;
    list-style: none;
  }

  li:hover {
    box-shadow: 0 0 6px rgb(35 173 255);
  }
</style>
