<template>
    <h4>Создание поста</h4>
    <form class="row" @submit.prevent>
      <div class="mb-3">
        <label for="title" class="form-label w-100">
          Название
          <input
            type="text"
            class="form-control"
            id="title"
            placeholder="Супер-пост"
            v-model="post.title"
          >
        </label>
      </div>
      <div class="mb-3">
        <label for="body" class="form-label w-100">
          Содержимое
          <textarea
            class="form-control"
            id="body"
            rows="3"
            placeholder="Очень крутой пост"
            v-model="post.body"
          ></textarea>
        </label>
      </div>
      <div class="d-grid gap-2 d-md-flex justify-content-md-end">
        <button
          type="button"
          class="btn btn-primary"
          @click="createPost"
        >
          Создать
        </button>
      </div>
    </form>
</template>

<script>
import _ from 'lodash';

export default {
  data() {
    return {
      post: {
        title: '',
        body: '',
      },
    };
  },
  methods: {
    createPost() {
      this.post.id = _.uniqueId();
      this.$emit('create', this.post);
      this.post = {
        title: '',
        body: '',
      };
    },
  },
};
</script>
