<template>
  <div>
    <h1>{{ msg }}</h1>
    <table>
      <thead>
        <tr>
          <th>User Id</th>
          <th>Id</th>
          <th>Title</th>
          <th>Body</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="post in getPosts" :key="post.id">
          <td>{{ post.userId }}</td>
          <td>{{ post.id }}</td>
          <td>{{ post.title }}</td>
          <td>{{ post.body }}</td>
        </tr>
      </tbody>
    </table>
  </div>
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