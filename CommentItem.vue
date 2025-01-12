<script>
export default {
  name: 'CommentItem',
  props: {
    username: String,
    comment: String,
    date: String,
  },
  methods: {
    handleDelete() {
      this.$emit('delete');
    }
  }
};
</script>

<template>
  <div class="comment-item">
    <div class="comment-header">
      <span class="username">{{ username }}</span>
      <span class="date">{{ date }}</span>
    </div>
    <p class="comment">{{ comment }}</p>
    <button @click="handleDelete" class="delete-btn">
      <i class="fa fa-trash"></i> Hapus
    </button>
  </div>
</template>

<style scoped>
.comment-item {
  background-color: #fff;
  padding: 15px;
  border-radius: 10px;
  margin-bottom: 15px;
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.1);
  transition: transform 0.3s ease, box-shadow 0.3s ease;
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
