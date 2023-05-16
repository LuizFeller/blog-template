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
      formData: {
        title: "",
        content: "",
      }
    };
  },

/* Indice
for(const algumacoisa in posts) */

/* Valor
for(const algumacoisa of posts)*/

methods: {
  handleClick (event) {
    //adicionar o post à lista de posts
    
    const now = new Date();

    const dataDaPostagem = `${now.getDate()}/${now.getMonth() + 1}/${now.getFullYear()}`;

    //metodo 1:
    /* this.posts[this.posts.length] = {
    title: this.formData.title,
    content: this.formData.content,
    }; */

    
    //metodo 2:
    this.posts.push({
      title: this.formData.title,
      content: this.formData.content,
      datetime: dataDaPostagem
    });

    this.formData = {
      title: "",
      content: "",
    }
  },

  handleInputChange(event) {
    const {name, value} = event.target;
    this.formData[name]=value;
 }
  
  /* console.log(event.target.classList); */
  
  /* estas duas constantes fazerm a mesma coisa que a seguinte abaixo: */
  /* const name = event.target.name; */
  /* const value = event.target.value; */

  },
};

</script>

<template>
  <div id="Lista-posts">
    <div class="post" v-for="post in posts" :key="post.title">
      <h3>{{ post.title }}</h3>
      <h4>{{ post.datetime }}</h4>
      <p>{{ post.content }}</p>
    </div>
  </div>

  <p>Titulo aqui -> {{ formData.title }}</p>
  <p>Conteudo aqui ->{{ formData.content }}</p>

  <form>
    <input
    name="title"
    :value="formData.title"
    @keyup="handleInputChange"
    placeholder="Titulo"/>
    <textarea

    name="content"
    :value="formData.content"
    @keyup="handleInputChange"
    placeholder="Escreva seu post aqui ..."
    id=""
    cols="30"
    rows="10"
    ></textarea>

  <!-- <form action="">
    <input type="text" />
    <textarea name="content" id="" cols="30" rows="10"></textarea> -->

    <button type="button" @click="handleClick">Salvar</button>
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
  

  /*CSS (16052023)*/

  text-align: center;
}
  
  input, textarea {
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
