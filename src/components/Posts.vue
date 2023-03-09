<template lang="pug">
div.container
  div.row
    div.col
      h1 {{ msg }}
      table.table.table-striped
        thead
          tr
            th UserId
            th Id
            th Title
            th Body
        tbody
          tr(v-for="post in getPosts" :key="post.id")
            td {{ post.userId }}
            td {{ post.id }}
            td {{ post.title }}
            td {{ post.body }}
</template>

<script setup>
import { ref, onMounted, computed } from 'vue';
import { usePostStore } from '../store/posts';

const store = usePostStore();
const msg = ref("Posts");
const getPosts = computed(() => {
  return store.getPosts;
});
const posts = computed(() => {
  return store.posts;
});
onMounted(() => {
  store.fetchPosts();
});
</script>

<style lang="scss">
table {
  border-collapse: collapse;
  width: 100%;
  font-family: Arial, Helvetica, sans-serif;
  font-size: 16px;
  th {
    border: 1px solid #ddd;
    padding: 8px;
    text-align: center;
    color: black;
  }
  td {
    border: 1px solid #ddd;
    padding: 8px;
  }
}

tr:nth-child(even) {
  background-color: #ecebeb;
}

tr:hover {
  background-color: #ddd;
}

h1 {
  text-align: center;
}
</style>