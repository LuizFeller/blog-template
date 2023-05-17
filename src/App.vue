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
  <RouterLink to="/">Home</RouterLink>
  <RouterLink to="/create">Novo Post</RouterLink>

  <RouterView :posts="posts" @create-post="addPost" />
</template>

<style scoped>
input,
textarea {
  width: 80%;

  padding: 12px 20px;
  margin: 8px 60px;
  box-sizing: border-box;
  border-radius: 10px;
  background-color: rgb(0, 255, 251);
  color: white;
}

button {
  width: 20%;

  padding: 10px 2px;
  margin: 8px 300px;
  box-sizing: border-box;
  border-radius: 10px;
  background-color: rgb(221, 255, 0);
  color: black;
}
</style>
