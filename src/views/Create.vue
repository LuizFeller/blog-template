<script>
export default {
  data() {
    return {
      formData: {
        title: "",
        content: "",
      },
    };
  },

  methods: {
    handleClick(event) {
      if (!this.formData.title) {
        alert("preencha o título do post");
        return;
      }

      //adicionar o post à lista de posts
      const now = new Date();

      const dataDaPostagem = `${now.getDate()}/${
        now.getMonth() + 1
      }/${now.getFullYear()}`;

      //metodo 1:
      /* this.posts[this.posts.length] = {
    title: this.formData.title,
    content: this.formData.content,
    }; */

      //metodo 2:
      /* this.posts.push({
        title: this.formData.title,
        content: this.formData.content,
        datetime: dataDaPostagem,
      }); */
      //emitir o evento create-post
      const newPost = {
        title: this.formData.title,
        content: this.formData.content,
        datetime: dataDaPostagem,
      };

      //emitir o evento create-post
      this.$emit("create-post", newPost);

      this.formData = {
        title: "",
        content: "",
      };
      this.$router.push("/");
    },

    handleInputChange(event) {
      const { name, value } = event.target;
      this.formData[name] = value;
    },

    /* console.log(event.target.classList); */

    /* estas duas constantes fazerm a mesma coisa que a seguinte abaixo: */
    /* const name = event.target.name; */
    /* const value = event.target.value; */
  },
};
</script>

<template>
  <form>
    <input
      name="title"
      :value="formData.title"
      @keyup="handleInputChange"
      placeholder="Titulo"
    />
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
</template>
