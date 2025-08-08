<template>
  <h1>Quản lý sách</h1>
  <FormSachComponent />
  <div class="container">
    <button type="button" class="btn btn-outline-success">Add</button>
    <button type="button" class="btn btn-outline-primary">Update</button>
  </div>

  <table class="table container">
    <thead>
      <tr>
        <th scope="col">ID</th>
        <th scope="col">Tên</th>
        <th scope="col">Loại</th>
        <th scope="col">Tác giả</th>
        <th scope="col">Giá</th>
        <th scope="col">Hành động</th>
      </tr>
    </thead>
    <tbody>
      <template v-for="item in listSach" :key="item.id">
        <tr>
          <td>{{ item.id }}</td>
          <td>{{ item.ten }}</td>
          <td>{{ item.loai }}</td>
          <td>{{ item.tacGia }}</td>
          <td>{{ item.gia }}</td>
          <td>
            <button type="button" class="btn btn-outline-primary">Detail</button>
            <button type="button" class="btn btn-outline-danger">Delete</button>
          </td>
        </tr>
      </template>
    </tbody>
  </table>
</template>

<script setup>
import FormSachComponent from '@/components/FormSachComponent.vue'
import { ref } from 'vue'
const listSach = ref([
  {
    // liet ke cac thuoc tinh cua sach
    id: 1,
    ten: 'Sach 1',
    loai: 'Loai 1',
    tacGia: 'Tac Gia 1',
    gia: 100000,
  },
  {
    id: 2,
    ten: 'Sach 2',
    loai: 'Loai 2',
    tacGia: 'Tac Gia 2',
    gia: 150000,
  },
  {
    id: 3,
    ten: 'Sach 3',
    loai: 'Loai 1',
    tacGia: 'Tac Gia 3',
    gia: 80000,
  },
  {
    id: 4,
    ten: 'Sach 4',
    loai: 'Loai 3',
    tacGia: 'Tac Gia 4',
    gia: 120000,
  },
  {
    id: 5,
    ten: 'Sach 5',
    loai: 'Loai 2',
    tacGia: 'Tac Gia 5',
    gia: 90000,
  },
])
</script>

<style scoped>
h1 {
  text-align: center;
}
button {
  margin-right: 50px;
}
</style>
