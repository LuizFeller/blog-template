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
  margin: 8px 90px;
  box-sizing: border-box;
  border-radius: 15px;
  background-color: rgb(0, 255, 251);
  color: white;
  font-size: 16px;
  background-image: src= "../assets/search_icon.png";
}

button {
  width: 20%;
  margin: 8px 200px;
  display: inline-block;
  padding: 6px 2px;
  font-size: 24px;
  cursor: pointer;
  text-align: center;
  outline: none;
  color: #fff;
  background-color: #4caf50;
  border: none;
  border-radius: 30px;
  box-shadow: 0 10px #999;
}

button:hover {
  background-color: black;
}

button:active {
  background-color: #8e3e49;
  box-shadow: 10 10px #666;
  transform: translateY(10px);
}
</style>
