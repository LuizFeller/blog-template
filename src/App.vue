<script>
import { RouterLink, RouterView } from "vue-router";
import "@/assets/base.css";

export default {
  data() {
    return {
      posts: [],
    };
  },
  methods: {
    addPost(newPost) {
      //adicionar o novo post à lista de posts
      console.log(newPost);
      this.posts.push(newPost);
    },
  },
};

/* Indice
for(const algumacoisa in posts) */

/* Valor
for(const algumacoisa of posts)*/
</script>

<template>
  <header>
    <nav>
      <RouterLink to="/">Home</RouterLink>
      <RouterLink to="/create">Novo Post</RouterLink>
    </nav>
  </header>

  <RouterView :posts="posts" @create-post="addPost" />
</template>

<style scoped>
header {
  /* background-color: yellow; */

}

nav {
  display: flex;
  justify-content: space-evenly;
}
</style>
