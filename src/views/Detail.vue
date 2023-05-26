<script>
export default {
  props: {
    posts: Array,
  },
  data() {
    //acessa o parâmetro id uma única vez
    const id = this.$route.params.id;

    return {
      //expondo a variável id para ser acessível no template
      id: id,
      post: this.posts[id],
    };
  },
};
</script>

<template>
  <h2>
    {{ post.title }}
  </h2>
  <h4>{{ post.datetime }}</h4>

  <textarea readonly :value="post.content"></textarea>
</template>

<style>
textarea {
  resize: none;
  outline: none;
  border: black;
  width: 60%;
  height:30px;
  border-radius: 10px;
}
main {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}
</style>

