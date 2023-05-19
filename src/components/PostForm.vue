<script>
export default {
  props: {
    post: Object,
  },
  data() {
    return {
      formData: {
        title: this.post?.title || "",
        content: this.post?.content || "",
      },
    };
  },

  methods: {
    handleCreatePost(event) {
      if (!this.formData.title) {
        alert("preencha o título do post");
        return;
      }

      const now = new Date();

      const dataDaPostagem = `${now.getDate()}/${
        now.getMonth() + 1
      }/${now.getFullYear()}`;

      const newPost = {
        title: this.formData.title,
        content: this.formData.content,
        datetime: dataDaPostagem,
      };

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
      v-model="formData.content"
      placeholder="Escreva seu post aqui ..."
      id=""
      cols="30"
      rows="10"
    ></textarea>

    <button type="button" @click="handleCreatePost">Salvar</button>
  </form>
</template>
