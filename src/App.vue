<script>
import { RouterLink, RouterView } from "vue-router";
import "@/assets/base.css";

export default {
  data() {
    return {
      posts: [
        {
          title: "Meu primeiro Post",
          datetime: "18/05/2023",
          content: "Primeiro",
        },
        {
          title: "Meu segundo Post",
          datetime: "18/05/2023",
          content: "Segundo",
        },
        {
          title: "Meu terceiro Post",
          datetime: "18/05/2023",
          content: "Terceiro",
        },
      ],
    };
  },
  methods: {
    addPost(newPost) {
      //adicionar o novo post à lista de posts
      console.log(newPost);
      this.posts.push(newPost);
    },
    updatePost(upDatedPost, id) {
      this.posts[id] = upDatedPost;
    },
    removePost(id) {
      //como remover um post do array this.posts
      const minhaNovaLista = [];

      for (const index in this.posts) {
        if (index == id) {
          continue;
        }

        const post = this.posts[index];
        minhaNovaLista.push(post);
      }
      this.posts = minhaNovaLista;
    },
  },
};

/* Indice
for(const alguma coisa in posts) */

/* Valor
for(const alguma coisa of posts)*/
</script>

<template>
  <header>
    <nav>
      <RouterLink to="/">Home</RouterLink>
      <RouterLink to="/create">Novo Post</RouterLink>
    </nav>
  </header>
  <main>
    <RouterView
      :posts="posts"
      @create-post="addPost"
      @edit-post="updatePost"
      @delete-post="removePost"
    />
  </main>
</template>

<style scoped>
nav {
  display: flex;
  justify-content: space-around;
}

.nav-link {
  display: inline-block;
  padding: 10px 20px;
  margin-top: 10px;
  font-size: 16px;
  text-decoration: none;
  color: #333;
  background-color: #dddddd;
  border-radius: 5px;
  transition: background-color 0.3s ease-in-out;
}

.nav-link:hover {
  background-color: #6e88a7;
}
</style>
