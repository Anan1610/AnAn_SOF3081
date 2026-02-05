<script setup>
import { ref } from 'vue';

// 1. Tạo biến message với giá trị mặc định
const message = ref('Thông điệp ban đầu');

// 2. Viết hàm xử lý sự kiện khi bấm nút
const updateMessage = () => {
  message.value = 'Thông điệp đã được thay đổi!'; // Cập nhật giá trị mới
};
</script>

<template>
  <div class="container">
    <p class="message-text">{{ message }}</p> <button class="btn" @click="updateMessage">Thay đổi thông điệp</button> </div>
</template>

<style scoped>
/* Thêm một chút CSS để giao diện dễ nhìn hơn */
.container {
  padding: 50px;
  text-align: center;
}
.message-text {
  font-size: 1.5rem;
  margin-bottom: 20px;
  font-weight: bold;
}
.btn {
  padding: 10px 20px;
  background-color: #333;
  color: white;
  border: none;
  cursor: pointer;
  border-radius: 4px;
}
.btn:hover {
  background-color: #555;
}
</style>