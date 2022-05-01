<template>
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
</template>

<script>
export default {
  props: {
    posts: {
      type: Array,
      required: true,
    },
  },
};
</script>
