<template>
  <div class="container mb-3 mt-3">
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
            v-bind:value="title"
            @input="title = $event.target.value"
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
            v-bind:value="body"
            @input="body = $event.target.value"
          ></textarea>
        </label>
      </div>
      <div class="d-grid gap-2 d-md-flex justify-content-md-end">
        <button type="button" class="btn btn-primary" @click="createPost">Создать</button>
      </div>
    </form>
    <div
      class="post border border-primary mt-3"
      v-for="post in posts"
      :key="post.id"
    >
      <div>
        <strong>Название:</strong> {{ post.title }}
      </div>
      <div>
        <strong>Содержимое:</strong> {{ post.body }}
      </div>
    </div>
  </div>
</template>

<script>
import _ from 'lodash';

export default {
  data() {
    return {
      posts: [
        { id: 1, title: 'Post 1', body: 'Body of Post 1' },
        { id: 2, title: 'Post 2', body: 'Body of Post 2' },
        { id: 3, title: 'Post 3', body: 'Body of Post 3' },
        { id: 4, title: 'Post 4', body: 'Body of Post 4' },
      ],
      title: '',
      body: '',
    };
  },
  methods: {
    createPost() {
      const newPost = {
        id: _.uniqueId(),
        title: this.title,
        body: this.body,
      };
      this.posts = [
        ...this.posts, newPost,
      ];

      this.title = '';
      this.body = '';
    },
    synchTitleValue(event) {
      this.title = event.target.value;
    },
    synchBodyValue(event) {
      this.body = event.target.value;
    },
  },
};
</script>
