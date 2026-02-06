<template>
  <div>
    <div class="mb-3">
      <label class="form-label">Nhập điểm trung bình:</label>
      <input 
        type="number" 
        v-model.number="score" 
        class="form-control" 
        placeholder="Nhập điểm..." 
        min="0" 
        max="10" 
        step="0.1"
      >
    </div>
    
    <div v-if="score !== null && score !== ''">
      
      <div v-if="score < 0 || score > 10" class="alert alert-danger fw-bold">
        <i class="bi bi-exclamation-triangle-fill me-2"></i>
        Vui lòng chỉ nhập điểm từ 0 đến 10!
      </div>

      <template v-else>
        <div v-if="score < 5.0" class="alert alert-secondary">Xếp loại: <b>Yếu</b></div>
        <div v-else-if="score < 6.5" class="alert alert-warning">Xếp loại: <b>Trung bình</b></div>
        <div v-else-if="score < 8.0" class="alert alert-primary">Xếp loại: <b>Khá</b></div>
        <div v-else-if="score < 9.0" class="alert alert-success">Xếp loại: <b>Giỏi</b></div>
        <div v-else class="alert alert-info">Xếp loại: <b>Xuất sắc</b></div>
      </template>

    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue';
const score = ref(null);
</script>