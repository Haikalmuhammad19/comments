<template>
    <div class="comment-item">
      <div class="comment-header">
        <div class="avatar">
          <span>{{ username.charAt(0).toUpperCase() }}</span>
        </div>
        <div class="user-details">
          <p class="username">{{ username }}</p>
          <p class="date">{{ date }}</p>
        </div>
        <button class="delete-btn" @click="deleteComment">Hapus</button>
      </div>
      <p class="comment-text">{{ comment }}</p>
    </div>
  </template>
  
  <script>
  export default {
    props: {
      username: {
        type: String,
        required: true,
      },
      comment: {
        type: String,
        required: true,
      },
      date: {
        type: String,
        required: true,
      },
    },
    methods: {
      deleteComment() {
        this.$emit("deleteComment"); // Emit event untuk menghapus komentar
      },
    },
  };
  </script>
  
  <style scoped>
  .comment-item {
    background-color: white;
    border-radius: 8px;
    padding: 10px;
    margin-bottom: 20px;
    box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
    animation: fadeIn 0.5s ease-in-out;
    width: 100%;
  }
  
  .comment-header {
    display: flex;
    align-items: center;
    margin-bottom: 10px;
    justify-content: space-between;
  }
  
  .avatar {
    width: 50px;
    height: 50px;
    border-radius: 50%;
    background-color: #007bff;
    color: white;
    display: flex;
    align-items: center;
    justify-content: center;
    font-size: 1.4rem;
    font-weight: bold;
    margin-right: 15px;
  }
  
  .user-details {
    flex-grow: 1;
  }
  
  .username {
    font-size: 1.2rem;
    font-weight: bold;
    color: #333;
    margin: 0;
  }
  
  .date {
    font-size: 0.9rem;
    color: #777;
    margin: 0;
  }
  
  .comment-text {
    font-size: 1rem;
    color: #555;
    margin: 0;
    line-height: 1.6;
  }
  
  .delete-btn {
    background-color: #e74c3c;
    color: white;
    padding: 10px 15px;
    border: none;
    border-radius: 5px;
    cursor: pointer;
    font-size: 0.9rem;
    transition: background-color 0.3s;
  }
  
  .delete-btn:hover {
    background-color: #c0392b;
  }
  
  /* Animasi efek masuk */
  @keyframes fadeIn {
    from {
      opacity: 0;
      transform: translateY(10px);
    }
    to {
      opacity: 1;
      transform: translateY(0);
    }
  }
  </style>
  