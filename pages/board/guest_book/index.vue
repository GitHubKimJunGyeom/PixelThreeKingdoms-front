<template>
    <div class="guestbook-container">
      <div class="guestbook-header">
        <h2>방명록</h2>
      </div>
  
      <div v-if="showMessageForm" class="message-form">
        <input v-model="newMessageName" placeholder="이름" class="input-name" />
        <textarea v-model="newMessageContent" placeholder="메시지" class="input-message"></textarea>
        <button @click="submitMessage" class="submit-btn">작성</button>
        <button @click="closeMessageForm" class="cancel-btn">취소</button>
      </div>
  
      <div v-else>
        <button @click="openMessageForm" class="add-message-btn">방명록 남기기</button>
      </div>
  
      <div v-if="messages.length" class="message-list">
        <div v-for="(message, index) in messages" :key="index" class="message-item">
          <strong>{{ message.name }}</strong>
          <p>{{ message.content }}</p>
        </div>
      </div>
      <div v-else class="no-messages">방명록에 메시지가 없습니다.</div>
    </div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        messages: [],
        newMessageName: '',
        newMessageContent: '',
        showMessageForm: false,
      };
    },
    methods: {
      openMessageForm() {
        this.showMessageForm = true;
      },
      closeMessageForm() {
        this.showMessageForm = false;
        this.newMessageName = '';
        this.newMessageContent = '';
      },
      submitMessage() {
        if (this.newMessageName && this.newMessageContent) {
          this.messages.push({
            name: this.newMessageName,
            content: this.newMessageContent,
          });
          this.closeMessageForm();
        }
      },
    },
  };
  </script>
  
  <style scoped>
  .guestbook-container {
    width: 80%;
    margin: 0 auto;
    padding: 20px;
    background-color: #fff;
    border-radius: 8px;
  }
  
  .guestbook-header {
    text-align: center;
    margin-bottom: 20px;
  }
  
  .add-message-btn {
    padding: 8px 16px;
    background-color: #4caf50;
    color: white;
    border: none;
    border-radius: 4px;
    cursor: pointer;
  }
  
  .message-form {
    margin-top: 20px;
    display: flex;
    flex-direction: column;
  }
  
  .input-name, .input-message {
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
  
  .message-list {
    margin-top: 20px;
  }
  
  .message-item {
    background-color: #f9f9f9;
    padding: 15px;
    margin-bottom: 10px;
    border-radius: 4px;
  }
  
  .no-messages {
    text-align: center;
    margin-top: 20px;
    font-size: 18px;
    color: #888;
  }
  </style>
  