<script>
import CommentItem from './CommentItem.vue';

export default {
  name: 'CommentList',
  components: {
    CommentItem
  },
  data() {
    return {
      comments: [
        { username: 'wan', comment: 'ha.', date: '2024-11-16' },
        { username: 'tu', comment: 'hi', date: '2024-11-16' },
        { username: 'tri', comment: 'hu', date: '2024-11-17' },
        { username: 'por', comment: 'he.', date: '2024-11-18' },
        { username: 'paip', comment: 'ho', date: '2024-11-19' },
        { username: 'sik', comment: 'plis', date: '2024-11-20' },
        { username: 'sepen', comment: 'give alok', date: '2024-11-21' },
      ],
      newUsername: '',
      newComment: '',
      newDate: '',
    };
  },
  methods: {
    addComment() {
      if (this.newUsername && this.newComment && this.newDate) {
        this.comments.push({
          username: this.newUsername,
          comment: this.newComment,
          date: this.newDate
        });
        this.newUsername = '';
        this.newComment = '';
        this.newDate = '';
      } else {
        alert('Harap isi semua kolom!');
      }
    },
    deleteComment(index) {
      this.comments.splice(index, 1);
    }
  }
};
</script>

<template>
  <div class="comment-list">
    <div class="add-comment-form">
      <input v-model="newUsername" type="text" placeholder="Nama Pengguna" />
      <textarea v-model="newComment" placeholder="Tulis komentar..." rows="3"></textarea>
      <input v-model="newDate" type="date" />
      <button @click="addComment">Tambah Komentar</button>
    </div>
    <div class="comments-container">
      <CommentItem
        v-for="(comment, index) in comments"
        :key="index"
        :username="comment.username"
        :comment="comment.comment"
        :date="comment.date"
        @delete="deleteComment(index)"
      />
    </div>
  </div>
</template>

<style scoped>
.comment-list {
  max-width: 1000px;
  margin: 0 auto;
}

.add-comment-form {
  margin-bottom: 20px;
  display: flex;
  flex-direction: column;
  gap: 10px;
}

.add-comment-form input,
.add-comment-form textarea {
  padding: 10px;
  border-radius: 5px;
  border: 1px solid #ccc;
  font-size: 16px;
}

.add-comment-form button {
  background-color: #4CAF50;
  color: white;
  padding: 10px 20px;
  border: none;
  border-radius: 5px;
  cursor: pointer;
  font-size: 16px;
  transition: background-color 0.3s ease;
}

.add-comment-form button:hover {
  background-color: #45a049;
}

.comments-container {
  display: flex;
  flex-wrap: nowrap;
  gap: 20px;
  justify-content: flex-start;
  overflow-x: auto;
  padding: 10px 0;
}

.comment-item {
  flex: 0 0 auto;
  width: 250px;
  background-color: #fff;
  padding: 15px;
  border-radius: 10px;
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.1);
  transition: transform 0.3s ease;
}

.comment-item:hover {
  transform: scale(1.03);
  box-shadow: 0 6px 18px rgba(0, 0, 0, 0.2);
}

.comment-header {
  display: flex;
  justify-content: space-between;
  font-size: 14px;
  color: #888;
}

.username {
  font-weight: bold;
}

.comment {
  font-size: 16px;
  margin-top: 10px;
  color: #333;
}

.delete-btn {
  background-color: #f44336;
  color: white;
  padding: 8px 16px;
  border: none;
  border-radius: 20px;
  cursor: pointer;
  font-size: 14px;
  display: flex;
  align-items: center;
  gap: 8px;
  transition: background-color 0.3s ease, transform 0.3s ease;
}

.delete-btn:hover {
  background-color: #d32f2f;
  transform: scale(1.1);
}

.delete-btn i {
  font-size: 16px;
  transition: transform 0.3s ease;
}

.delete-btn:hover i {
  transform: rotate(360deg);
}
</style>
