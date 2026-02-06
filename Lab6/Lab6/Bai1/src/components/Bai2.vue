<template>
  <div>
    <div class="mb-3">
      <label class="form-label">Nhập tháng của bạn:</label>
      <input type="number" v-model.number="month" class="form-control">
    </div>

    <p v-if="month < 1 || month > 12" style="color: red; font-weight: bold;">
      Vui lòng nhập tháng từ 1 đến 12!
    </p>
    
    <template v-else>
      <p v-if="month <= 3" class="text-success fw-bold">Mùa Xuân</p>
      <p v-else-if="month <= 6" class="text-danger fw-bold">Mùa Hè</p>
      <p v-else-if="month <= 9" class="text-warning fw-bold">Mùa Thu</p>
      <p v-else class="text-info fw-bold">Mùa Đông</p>
    </template>
  </div>
</template>

<script setup>
import { ref } from 'vue';
const month = ref(1);
</script>