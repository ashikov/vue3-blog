<template>
  <div class="container mb-3 mt-3">
    <post-form
      @create="createPost"
    />
    <post-list
      :posts="posts"
    />
  </div>
</template>

<script>
import PostForm from './components/PostForm.vue';
import PostList from './components/PostList.vue';

export default {
  components: {
    PostForm,
    PostList,
  },
  data() {
    return {
      posts: [
        { id: 1, title: 'Post 1', body: 'Body of Post 1' },
        { id: 2, title: 'Post 2', body: 'Body of Post 2' },
        { id: 3, title: 'Post 3', body: 'Body of Post 3' },
        { id: 4, title: 'Post 4', body: 'Body of Post 4' },
      ],
    };
  },
  methods: {
    createPost(post) {
      this.posts = [...this.posts, post];
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
