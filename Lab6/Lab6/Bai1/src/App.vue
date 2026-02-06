<template>
  <div class="app-container">
    <header class="text-center py-4 bg-primary text-white mb-4 shadow-sm header-gradient">
      <h1 class="fw-bold">LAB 6 - VUEJS</h1>
      <p class="mb-0 opacity-75">Conditional & List Rendering</p>
    </header>

    <div class="container">
      <div class="row">
        <div class="col-md-3 mb-4">
          <div class="list-group shadow-sm sticky-top" style="top: 20px; z-index: 1;">
            <button 
              v-for="tab in tabs" 
              :key="tab.id"
              @click="activeTab = tab.id"
              class="list-group-item list-group-item-action d-flex justify-content-between align-items-center p-3 border-0"
              :class="{ 'active-tab': activeTab === tab.id }"
            >
              <span>
                <i class="bi bi-code-square me-2"></i> {{ tab.name }}
              </span>
              <span class="badge bg-light text-dark rounded-pill">{{ tab.desc }}</span>
            </button>
          </div>
        </div>

        <div class="col-md-9">
          <div class="card border-0 shadow-lg rounded-3 overflow-hidden">
            <div class="card-header bg-white p-4 border-bottom-0">
              <h2 class="text-primary fw-bold mb-0">
                {{ tabs.find(t => t.id === activeTab).name }}
              </h2>
              <small class="text-muted">{{ tabs.find(t => t.id === activeTab).fullDesc }}</small>
            </div>
            
            <div class="card-body p-4 bg-light bg-opacity-25">
              <transition name="fade" mode="out-in">
                <div :key="activeTab">
                  <Bai1 v-if="activeTab === 1" />
                  <Bai2 v-if="activeTab === 2" />
                  <Bai3 v-if="activeTab === 3" />
                  <Bai4 v-if="activeTab === 4" />
                </div>
              </transition>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue';
import Bai1 from './components/Bai1.vue';
import Bai2 from './components/Bai2.vue';
import Bai3 from './components/Bai3.vue';
import Bai4 from './components/Bai4.vue';

// Quản lý Tab đang hiển thị
const activeTab = ref(1);

// Danh sách các bài
const tabs = [
  { id: 1, name: 'Bài 1', desc: 'Điểm số', fullDesc: 'Xếp loại học sinh dựa trên điểm trung bình' },
  { id: 2, name: 'Bài 2', desc: 'Mùa', fullDesc: 'Xác định mùa trong năm theo tháng' },
  { id: 3, name: 'Bài 3', desc: 'Tin tức', fullDesc: 'Danh sách bài viết sức khỏe (List Rendering)' },
  { id: 4, name: 'Bài 4', desc: 'CRUD', fullDesc: 'Quản lý học sinh: Thêm, Sửa, Xóa' },
];
</script>

<style scoped>
/* Gradient đẹp cho Header */
.header-gradient {
  background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
}

/* Custom style cho Tab active */
.active-tab {
  background-color: #fff !important;
  color: #764ba2 !important;
  border-left: 5px solid #764ba2 !important;
  font-weight: bold;
  box-shadow: 0 4px 6px rgba(0,0,0,0.05);
}

.list-group-item {
  transition: all 0.3s ease;
  cursor: pointer;
}

.list-group-item:hover:not(.active-tab) {
  background-color: #f8f9fa;
  transform: translateX(5px);
}

/* Hiệu ứng chuyển cảnh mượt mà */
.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.3s ease;
}

.fade-enter-from,
.fade-leave-to {
  opacity: 0;
}
</style>