<template>
  <div class="container">
    <div class="row">
      <div class="col">
        <h1>{{ msg }}</h1>
        <table class="table table-striped">
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
    </div>
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

<style lang="scss">
table {
  border-collapse: collapse;
  width: 100%;
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