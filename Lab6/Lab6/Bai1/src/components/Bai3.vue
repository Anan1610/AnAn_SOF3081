<template>
  <div>
    <h3 class="text-center mb-4">Kiến thức sức khỏe cộng đồng</h3>
    <div class="row">
      <div class="col-md-4 mb-4" v-for="(item, index) in items" :key="index">
        <div class="card h-100">
          <img :src="item.image" class="card-img-top" alt="Image" style="height: 200px; object-fit: cover;">
          <div class="card-body">
            <h5 class="card-title">{{ item.title }}</h5>
            <p class="card-text">{{ item.content }}</p>
            <button class="btn btn-info text-white">Xem chi tiết</button>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue';

// Data mẫu dựa trên hình ảnh đề bài
const items = ref([
  {
    title: '8 loại rau củ quả giàu canxi',
    content: 'Canxi là khoáng chất cần thiết đối với cơ thể người. Có nhiều cách để bổ sung canxi...',
    image: 'https://suckhoedoisong.qltns.mediacdn.vn/324455921873985536/2023/3/15/vai-tro-cua-canxi1-1678874546755279038552.jpg'
  },
  {
    title: 'Các loại gia vị tốt cho sức khỏe',
    content: 'Một số loại gia vị cung cấp nhiều polyphenol chống oxy hóa cao hơn các loại gia vị quen thuộc khác...',
    image: 'https://maydonggoi.com.vn/wp-content/uploads/2024/03/gia-vi-la-gi-1-510x369.jpeg'
  },
  {
    title: '9 loại đậu bổ dưỡng nên dùng nhiều',
    content: 'Đậu lăng, đậu nành, đậu phộng, đậu Hà Lan giàu chất xơ, protein...',
    image: 'https://down-vn.img.susercontent.com/file/vn-11134207-7r98o-lkvstofiskaz8b'
  }
]);
</script>