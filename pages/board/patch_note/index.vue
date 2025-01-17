<template>
    <div class="board-container">
      <div class="board-header">
        <h2>patchnote</h2>
        <button class="add-post-btn" @click="openPostForm">글 작성</button>
      </div>
  
      <div v-if="showPostForm" class="post-form">
        <input v-model="newPostTitle" placeholder="제목" class="input-title" />
        <textarea v-model="newPostContent" placeholder="내용" class="input-content"></textarea>
        <button @click="submitPost" class="submit-btn">작성</button>
        <button @click="closePostForm" class="cancel-btn">취소</button>
      </div>
  
      <div v-if="posts.length" class="post-list">
        <div v-for="(post, index) in posts" :key="index" class="post-item">
          <h3>{{ post.title }}</h3>
          <p>{{ post.content }}</p>
          <button @click="deletePost(index)" class="delete-btn">삭제</button>
        </div>
      </div>
      <div v-else class="no-posts">게시글이 없습니다.</div>
    </div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        posts: [],
        newPostTitle: '',
        newPostContent: '',
        showPostForm: false,
      };
    },
    methods: {
      openPostForm() {
        this.showPostForm = true;
      },
      closePostForm() {
        this.showPostForm = false;
        this.newPostTitle = '';
        this.newPostContent = '';
      },
      submitPost() {
        if (this.newPostTitle && this.newPostContent) {
          this.posts.push({
            title: this.newPostTitle,
            content: this.newPostContent,
          });
          this.closePostForm();
        }
      },
      deletePost(index) {
        this.posts.splice(index, 1);
      },
    },
  };
  </script>
  
  <style scoped>
  .board-container {
    width: 80%;
    margin: 0 auto;
    padding: 20px;
    background-color: #fff;
    border-radius: 8px;
  }
  
  .board-header {
    display: flex;
    justify-content: space-between;
    align-items: center;
  }
  
  .add-post-btn {
    padding: 8px 16px;
    background-color: #4caf50;
    color: white;
    border: none;
    border-radius: 4px;
    cursor: pointer;
  }
  
  .post-form {
    margin-top: 20px;
    display: flex;
    flex-direction: column;
  }
  
  .input-title, .input-content {
    padding: 10px;
    margin: 10px 0;
    border: 1px solid #ccc;
    border-radius: 4px;
  }
  
  .submit-btn, .cancel-btn {
    padding: 10px 20px;
    margin-top: 10px;
    background-color: #4caf50;
    color: white;
    border: none;
    border-radius: 4px;
    cursor: pointer;
  }
  
  .cancel-btn {
    background-color: #f44336;
  }
  
  .post-list {
    margin-top: 20px;
  }
  
  .post-item {
    background-color: #f9f9f9;
    padding: 15px;
    margin-bottom: 10px;
    border-radius: 4px;
  }
  
  .delete-btn {
    padding: 5px 10px;
    background-color: #f44336;
    color: white;
    border: none;
    border-radius: 4px;
    cursor: pointer;
  }
  
  .no-posts {
    text-align: center;
    margin-top: 20px;
    font-size: 18px;
    color: #888;
  }
  </style>
  