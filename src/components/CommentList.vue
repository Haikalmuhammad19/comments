<template>
    <div class="comment-section">
      <!-- Form Input -->
      <div class="form-container">
        <h2>Bagikan Komentar Anda</h2>
        <input
          v-model="newUsername"
          class="input"
          type="text"
          placeholder="Nama Anda"
        />
        <textarea
          v-model="newComment"
          class="textarea"
          rows="4"
          placeholder="Tulis komentar Anda di sini..."
        ></textarea>
        <button class="btn" @click="addComment">Tambahkan Komentar</button>
      </div>
  
      <!-- Daftar Komentar -->
      <div class="comment-list">
        <CommentItem
          v-for="(comment, index) in comments"
          :key="index"
          :username="comment.username"
          :comment="comment.text"
          :date="comment.date"
          @deleteComment="deleteComment(index)"
        />
      </div>
    </div>
  </template>
  
  <script>
  import CommentItem from "./CommentItem.vue";
  
  export default {
    components: {
      CommentItem,
    },
    data() {
      return {
        comments: [
          { username: "Haikal Muhammad Kurniawan", text: "Sangat inspiratif!", date: "2024-11-15" },
          { username: "Haikal", text: "Tulisannya sangat bermanfaat!", date: "2024-11-14" },
        ],
        newUsername: "",
        newComment: "",
      };
    },
    methods: {
      addComment() {
        if (this.newUsername && this.newComment) {
          this.comments.push({
            username: this.newUsername,
            text: this.newComment,
            date: new Date().toISOString().split("T")[0],
          });
          this.newUsername = "";
          this.newComment = "";
        }
      },
      deleteComment(index) {
        this.comments.splice(index, 1); // Menghapus komentar berdasarkan index
      },
    },
  };
  </script>
  
  <style scoped>
  /* Styling tetap sama */
  .comment-section {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: flex-start;
    width: 100vw; /* Lebar penuh */
    height: 100vh; /* Tinggi penuh */
    background-color: #f4f4f9;
    padding: 10px;
    box-sizing: border-box;
    overflow-y: auto;
  }
  
  /* Form input komentar */
  .form-container {
    width: 80%; /* Memenuhi sebagian besar layar */
    max-width: 900px; /* Batas maksimal */
    background: white;
    padding: 30px;
    border-radius: 10px;
    box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
    margin-bottom: 30px;
  }
  
  .form-container h2 {
    margin-bottom: 15px;
    color: #333;
    text-align: center;
  }
  
  .input,
  .textarea {
    width: 100%;
    padding: 5px;
    margin-bottom: 15px;
    border: 1px solid #ddd;
    border-radius: 8px;
    font-size: 1.1rem;
    outline: none;
    transition: border-color 0.3s;
  }
  
  .input:focus,
  .textarea:focus {
    border-color: #007bff;
    box-shadow: 0 0 5px rgba(0, 123, 255, 0.5);
  }
  
  .btn {
    width: 100%;
    padding: 15px;
    background-color: #007bff;
    color: white;
    font-size: 1.2rem;
    font-weight: bold;
    border: none;
    border-radius: 8px;
    cursor: pointer;
    transition: background-color 0.3s, transform 0.2s;
  }
  
  .btn:hover {
    background-color: #0056b3;
    transform: scale(1.02);
  }
  
  /* Daftar komentar */
  .comment-list {
    width: 100%;
    max-width: 900px;
    margin-top: 10px;
  }
  
  @media (max-width: 768px) {
    .form-container {
      padding: 15px;
    }
  
    .input,
    .textarea {
      font-size: 1rem;
    }
  
    .btn {
      font-size: 1rem;
    }
  }
  </style>
  