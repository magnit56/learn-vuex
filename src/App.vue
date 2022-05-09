<template>
  <div id="app">
    <PostForm />
    <h1>{{ postsCount }}</h1>
    <div v-for="post in validPosts" :key="post.id" class="post">
      <h2>{{ post.title }}</h2>
      <p>{{ post.body }}</p>
    </div>
  </div>
</template>

<script>
import { mapGetters, mapActions } from 'vuex';
import PostForm from './components/PostForm.vue';

export default {
  name: 'app',
  // data() {
  //   return {
  //     posts: [],
  //   }
  // },
  // computed: {
  //   allPosts() {
  //     return this.$store.getters.allPosts;
  //   }
  // },
  computed: mapGetters(["allPosts", "postsCount", "validPosts"]),
  methods: mapActions(["fetchPosts"]),
  async mounted() {
    // await this.$store.dispatch("fetchPosts")
    this.fetchPosts();
  },
  components: {
    PostForm,
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin: 60px auto;
  width: 400px;
}
.post {
  border: 1px solid #ccc;
  border-radius: 5px;
  margin-bottom: 1rem;
}
</style>
