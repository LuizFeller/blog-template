<script>
import { RouterLink } from "vue-router";

export default {
  props: {
    posts: Array,
  },
  data() {
    return {
      search: "",
      showModal: false,
    };
  },

  computed: {
    filteredPosts() {
      //se search estiver vazio, retorne a lista completa de posts
      if (!this.search) return this.posts;

      //se tiver qualquer coisa em search, faz o filtro
      const listaFiltrada = [];

      for (const post of this.posts) {
        if (post.title.includes(this.search)) {
          listaFiltrada.push(post);

          /*    for (const post of this.posts) {
        if (this.search && post.title.includes(this.search)) {
          listaFiltrada.push(post); */
        }
      }
      return listaFiltrada;
    },
  },
  methods: {
    getPostId(title) {
      //passa pela lista de posts (não filtrada)
      for (const index in this.posts) {
        //acessa o post na posição index da lista de posts
        const post = this.posts[index];
        //verifica se o título do post atual é igual ao título buscado
        if (post.title === title) return index;
      }
    },
    /* handledCLick() {
      console.log("Oi pessoal");
    }, */

    toggle() {
      this.showModal = !this.showModal;
    },
  },
};
</script>

<template>
  <input v-model="search" placeholder="Procure pelo título do post ..." />
  <div id="Lista-posts">
    <div class="post" v-for="post in filteredPosts" :key="post.key">
      <h3>
        {{ post.title }}
        <RouterLink :to="`/edit/${getPostId(post.title)}`">
          <span class="material-symbols-rounded">edit</span>
        </RouterLink>
        <span class="material-symbols-rounded" @click="toggle">close</span>
      </h3>
      <h4>{{ post.datetime }}</h4>
      <p>{{ post.content }}</p>
    </div>
  </div>
  <div class="modal" v-show="showModal">
    <div class="modal-content">
      <h3>Deletar Post</h3>
      <p>Tem certeza que deseja deletar o 'Titulo do post'?</p>
      <p>Esta ação é irreversivel</p>

      <div class="modal-actions">
        <button class="bg-sucess" @click="deletePost">Confirmar</button>
        <button class="bg-error" @click="toggle">Cancelar</button>
      </div>
    </div>
  </div>
</template>
