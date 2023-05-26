<script>
export default {
  props: {
    post: Object,
    id: String,
  },
  data() {
    return {
      formData: {
        title: this.post?.title || "",
        content: this.post?.content || "",
      },
      isEditing: Boolean(this.post),
    };
  },

  methods: {
    handleCreatePost(event) {
      if (!this.formData.title) {
        alert("preencha o título do post");
        return;
      }
      //adicionar o post à lista posts
      const now = new Date();

      const dataDaPostagem = `${now.getDate()}/${
        now.getMonth() + 1
      }/${now.getFullYear()} - ${now.getHours()}:${now.getMinutes()}:${now.getSeconds()}`;

      /* now.getMonth() + 1
      } - ${now.getFullYear()} - ${now.getHours()}:${now.getMinutes()}:${now.getSeconds()}`; */

      //método 1
      //this.posts[this.posts.length] = {
      //title: this.formData.title,
      //content: this.formData.content,
      //};

      const postData = {
        title: this.formData.title,
        content: this.formData.content,
        datetime: dataDaPostagem,
      };

      if (this.isEditing) {
        this.$emit("edit-post", postData, this.id);
      } else {
        this.$emit("create-post", postData);
      }

      /* this.formData = {
        title: "",
        content: "",
      }; */

      this.$router.push("/");
    },

    /* handleInputChange(event) {
      const { name, value } = event.target;
      this.formData[name] = value;
    }, */
  },
};
</script>

<template>
  <!-- ID passado pelo meu pai:
  {{ id }} -->
  <form>
    <input v-model="formData.title" placeholder="Título" />

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

<style scoped>
form {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  padding: 20px;
  margin-top: 30px;
  border-radius: 30px;
}

form > input {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  text-align: center;
  width: 80%;
}

form > * {
  margin: 1rem;
  border: 0rem;
  outline: 40px;
  padding: 40px;
  font-size: 20px;
  border-radius: 20px;
  width: 100%;
  background-color: whitesmoke;
  transition-delay: 0, 4s;
}

form > input:focus,
form > textarea:focus {
  border: px solid #ccc;
  background-color: rgb(176, 160, 160);
}

form button {
  background-color: #3c3c75;
  color: white;
  font-size: 20px;
  padding: 8px 10px;
  border: none;
  border-radius: 20px;
  cursor: pointer;
  transition: all 0.3s ease-in-out;
}

form button:hover {
  background-color: rgb(85, 126, 85);
}
</style>
