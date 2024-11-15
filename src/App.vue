<template>
  <div id="app">
    <h1>Sistem Komentar</h1>
    <CommentList />
  </div>
</template>

<script>
import CommentList from './components/CommentList.vue';

export default {
  components: {
    CommentList,
  },
};
</script>

<style>
/* Mengatur seluruh halaman agar tidak dapat digeser */
body, html {
  height: 100%;   /* Pastikan tinggi halaman penuh */
  margin: 0;      /* Hilangkan margin default */
  padding: 0;     /* Hilangkan padding default */
  overflow: hidden; /* Menghindari halaman digulung */
}

#app {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  height: 100%; /* Memastikan div utama mengisi seluruh tinggi layar */
  background-color: #f4f4f9;
  box-sizing: border-box;
  padding: 20px;
}

h1 {
  font-size: 2rem;
  margin-bottom: 20px;
  color: #333;
}
</style>
