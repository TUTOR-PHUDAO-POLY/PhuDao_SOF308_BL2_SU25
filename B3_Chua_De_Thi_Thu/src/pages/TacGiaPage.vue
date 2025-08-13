<template>
  <h1>Quản lý sách</h1>
  <FormTacGiaComponent v-model:tacGia="formTacGia" />
  <div class="container">
    <button type="button" class="btn btn-outline-success" @click="addTacGia()">Add</button>
    <button type="button" class="btn btn-outline-primary" @click="updateTacGia()">Update</button>
  </div>

  <table class="table container">
    <thead>
      <tr>
        <th scope="col">ID</th>
        <th scope="col">Tên</th>
        <th scope="col">Giới tính</th>
        <th scope="col">Địa chỉ</th>
        <th scope="col">Tuổi</th>
        <th scope="col">Hành động</th>
      </tr>
    </thead>
    <tbody>
      <template v-for="(item, index) in listTacGia" :key="item.id">
        <tr>
          <td>{{ item.id }}</td>
          <td>{{ item.ten }}</td>
          <td>{{ item.gioiTinh ? 'Nam' : 'Nữ' }}</td>
          <td>{{ item.diaChi }}</td>
          <td>{{ item.tuoi }}</td>
          <td>
            <button type="button" class="btn btn-outline-danger" @click="removeTacGia(index)">
              Delete
            </button>
            <button type="button" class="btn btn-outline-warning" @click="detailTacGia(item)">
              Detail
            </button>
          </td>
        </tr>
      </template>
    </tbody>
  </table>
</template>

<script setup>
import FormTacGiaComponent from '@/components/FormTacGiaComponent.vue'
import { ref } from 'vue'
const listTacGia = ref([
  {
    ten: 'ten 1',
    gioiTinh: true,
    diaChi: 'diaChi 1',
    tuoi: 66,
    id: '1',
  },
  {
    ten: 'ten 2',
    gioiTinh: false,
    diaChi: 'diaChi 2',
    tuoi: 18,
    id: '2',
  },
  {
    ten: 'ten 3',
    gioiTinh: true,
    diaChi: 'diaChi 3',
    tuoi: 69,
    id: '3',
  },
  {
    ten: 'ten 4',
    gioiTinh: false,
    diaChi: 'diaChi 4',
    tuoi: 62,
    id: '4',
  },
  {
    ten: 'ten 5',
    gioiTinh: false,
    diaChi: 'diaChi 5',
    tuoi: 50,
    id: '5',
  },
  {
    ten: 'ten 6',
    gioiTinh: true,
    diaChi: 'diaChi 6',
    tuoi: 75,
    id: '6',
  },
  {
    ten: 'ten 7',
    gioiTinh: false,
    diaChi: 'diaChi 7',
    tuoi: 36,
    id: '7',
  },
  {
    ten: 'ten 8',
    gioiTinh: true,
    diaChi: 'diaChi 8',
    tuoi: 93,
    id: '8',
  },
  {
    ten: 'ten 9',
    gioiTinh: false,
    diaChi: 'diaChi 9',
    tuoi: 82,
    id: '9',
  },
  {
    ten: 'ten 10',
    gioiTinh: false,
    diaChi: 'diaChi 10',
    tuoi: 67,
    id: '10',
  },
  {
    ten: 'ten 11',
    gioiTinh: false,
    diaChi: 'diaChi 11',
    tuoi: 75,
    id: '11',
  },
  {
    ten: 'ten 12',
    gioiTinh: false,
    diaChi: 'diaChi 12',
    tuoi: 14,
    id: '12',
  },
  {
    ten: 'ten 13',
    gioiTinh: false,
    diaChi: 'diaChi 13',
    tuoi: 24,
    id: '13',
  },
])
const formTacGia = ref({
  ten: '',
  gioiTinh: false,
  diaChi: '',
  tuoi: 0,
})
const idTacGiaUpdate = ref(-1)
function removeTacGia(i) {
  listTacGia.value.splice(i, 1)
}
function detailTacGia(item) {
  formTacGia.value = { ...item }
  idTacGiaUpdate.value = item.id
}
function resetData() {
  formTacGia.value = {
    ten: '',
    gioiTinh: false,
    diaChi: '',
    tuoi: 0,
  }
  idTacGiaUpdate.value = -1
}
function addTacGia() {
  listTacGia.value.push({
    ...formTacGia.value,
    id: (listTacGia.value.length + 1).toString(),
  })
  resetData()
}
function updateTacGia() {
  listTacGia.value[idTacGiaUpdate.value] = {
    ...formTacGia.value,
  }
  resetData()
}
</script>

<style scoped>
h1 {
  text-align: center;
}
button {
  margin-right: 50px;
}
</style>
