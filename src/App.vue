<script>
import { RouterLink, RouterView } from "vue-router";

export default {
  data() {
    return {
      posts: [
        {
          title: "Meu Primeiro Post",
          datetime: Date.now(),
          content: "Postar aqui é muito legal",
        },
        {
          title: "Meu Primeiro Post",
          datetime: Date.now(),
          content: "Postar aqui é muito legal",
        },
      ],
    };
  },
};
/* Indice
for(const algumacoisa in posts) */

/* Valor
for(const algumacoisa of posts)*/
</script>

<template>
  <div id="Lista-posts">
    <div class="post" v-for="post in posts" :key="post.title">
      <h3>{{ post.title }}</h3>
      <h4>{{ post.datetime }}</h4>
      <p>{{ post.content }}</p>
    </div>
  </div>

  <form action="">
    <input type="text" />
    <textarea name="content" id="" cols="30" rows="10"></textarea>
    <button type="submit">Criar</button>
  </form>

  <RouterView />
</template>

<style scoped>
form {
  display: flex;
  flex-direction: column;
}

form > * {
  margin: 1rem;
}
</style>
