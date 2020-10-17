<template>
  <div class="add-news">
    <span>Редактировать новость:</span>
    <input type="text" v-model="title" :placeholder="title">
    <textarea v-model="content" :placeholder="content"></textarea>
    <button @click="editNews">Сохранить</button>
  </div>
</template>

<script>
export default {
  name: "_id",

  data() {
    return {
      title: '',
      content: '',
      id: this.$route.params.id,
    }
  },

  methods: {
    editNews() {
      this.$fireStore.collection('news').doc(this.id).set({
        title: this.title,
        content: this.content,
      });

      this.title = '';
      this.content = '';
    }
  },

  async asyncData({$fireStore, route}) {

    const newsId = route.params.id;
    const newsRef = $fireStore.collection("news").doc(newsId);
    const arr = [];

    await newsRef.get().then(function(doc) {
      arr.push(doc.data());
    }).catch(function(error) {
      console.log(error);
    });

    return {
      title: arr[0].title,
      content: arr[0].content,
    };
  }
}
</script>

<style scoped>

</style>
