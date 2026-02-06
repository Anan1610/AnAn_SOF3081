<template>
  <div class="row">
    <div class="col-md-5">
      <div class="card p-3 mb-4">
        <h4>{{ isEditing ? 'Cập nhật học sinh' : 'Thêm học sinh' }}</h4>
        <form @submit.prevent="submitForm">
          <div class="mb-3">
            <label class="form-label">Họ tên:</label>
            <input type="text" v-model="student.name" class="form-control" required>
          </div>
          <div class="mb-3">
            <label class="form-label">Điểm:</label>
            <input type="number" v-model="student.score" class="form-control" min="0" max="10" required>
          </div>
          <div class="mb-3">
            <label class="form-label">Ngày sinh:</label>
            <input type="date" v-model="student.dob" class="form-control" required>
          </div>
          
          <button type="submit" :class="isEditing ? 'btn btn-primary' : 'btn btn-success'">
            {{ isEditing ? 'Cập nhật' : 'Thêm' }}
          </button>
          <button v-if="isEditing" type="button" class="btn btn-secondary ms-2" @click="resetForm">Hủy</button>
        </form>
      </div>
    </div>

    <div class="col-md-7">
      <h3>Danh sách học sinh</h3>
      <table class="table table-bordered table-hover">
        <thead>
          <tr>
            <th>Họ và tên</th>
            <th>Điểm</th>
            <th>Ngày sinh</th>
            <th>Hành động</th>
          </tr>
        </thead>
        <tbody>
          <tr v-for="(stu, index) in students" :key="index">
            <td>{{ stu.name }}</td>
            <td>{{ stu.score }}</td>
            <td>{{ stu.dob }}</td>
            <td>
              <button class="btn btn-warning btn-sm me-2" @click="editStudent(index)">Sửa</button>
              <button class="btn btn-danger btn-sm" @click="deleteStudent(index)">Xóa</button>
            </td>
          </tr>
        </tbody>
      </table>
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue';

// State quản lý danh sách và form
const students = ref([
  { name: 'Nguyễn Chí Hùng', score: 8, dob: '2006-01-01' },
  { name: 'Phạm Thị Lan', score: 9, dob: '2006-05-15' }
]);

const student = ref({ name: '', score: null, dob: '' });
const isEditing = ref(false);
const editingIndex = ref(null);

// Hàm xử lý Submit (Dùng chung cho Thêm và Sửa)
function submitForm() {
  if (isEditing.value) {
    // Logic cập nhật: update phần tử tại vị trí editingIndex
    students.value[editingIndex.value] = { ...student.value };
    isEditing.value = false;
    editingIndex.value = null;
  } else {
    // Logic thêm mới: push vào mảng
    students.value.push({ ...student.value });
  }
  // Reset form sau khi submit
  resetForm(); 
}

// Hàm nạp dữ liệu lên form để sửa
function editStudent(index) {
  student.value = { ...students.value[index] }; // Copy object để tránh tham chiếu
  isEditing.value = true;
  editingIndex.value = index;
}

// Hàm xóa học sinh
function deleteStudent(index) {
  if (confirm('Bạn có chắc muốn xóa học sinh này?')) {
    students.value.splice(index, 1);
  }
}

// Hàm làm mới form
function resetForm() {
  student.value = { name: '', score: null, dob: '' };
  // Nếu đang ở chế độ edit mà bấm hủy thì tắt edit mode
  if(isEditing.value && !student.value.name) {
      isEditing.value = false;
      editingIndex.value = null;
  }
}
</script>