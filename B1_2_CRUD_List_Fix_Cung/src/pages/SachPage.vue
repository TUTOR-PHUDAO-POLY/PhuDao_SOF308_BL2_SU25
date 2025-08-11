<template>
  <h1>Quản lý sách</h1>
  <FormSachComponent v-model:book="formBook" />
  <div class="container">
    <!-- Truy gia tri tu componnetn cha => con: props, event: emits
     vue 3.4 + => v-model
     -->
    <button type="button" class="btn btn-outline-success" @click="addBook()">Add</button>
    <button type="button" class="btn btn-outline-primary" @click="updateBook()">Update</button>
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
      <template v-for="(item, i) in listSach" :key="item.id">
        <tr>
          <td>{{ item.id }}</td>
          <td>{{ item.ten }}</td>
          <td>{{ item.loai }}</td>
          <td>{{ item.tacGia }}</td>
          <td>{{ item.gia }}</td>
          <td>
            <button type="button" class="btn btn-outline-primary" @click="detailBook(item)">
              Detail
            </button>
            <!-- <button type="button" class="btn btn-outline-danger"
            @click="deleteBook(item.id)">
              Delete
            </button> -->
            <!-- i nay dai dien cho index  -->
            <button type="button" class="btn btn-outline-danger" @click="deleteBook1(i)">
              Delete
            </button>
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
// -1 ban dau reset ban dau - chua update
const idUpdate = ref(-1)
const formBook = ref({
  ten: '',
  loai: '',
  tacGia: '',
  gia: 0,
})
// function deleteBook(id1) {
//   // delete(index)
//   // splice(index,1)
//   // B1: Tim index cua sach can xoa => for - cach cu, findIndex
//   const index = listSach.value.findIndex((b) => b.id === id1)
//   // B2: Xoa phan tu tai index do
//   listSach.value.splice(index, 1)
// }
function deleteBook1(index) {
  // Xoa phan tu tai index
  listSach.value.splice(index, 1)
}
function detailBook(item) {
  // copy thong so cua object item vao formBook
  formBook.value = { ...item } // Sao chep toan bo thuoc tinh cua item vao formBook
  idUpdate.value = item.id // Luu id de update
}
function resetForm() {
  formBook.value = {
    ten: '',
    loai: '',
    tacGia: '',
    gia: 0,
  }
}
function addBook() {
  // validate formBook
  // add
  listSach.value.push({
    id: listSach.value.length + 1, // Tự động tăng ID
    ...formBook.value, // Sao chép các thuộc tính từ formBook
  })
  // moi truong hop add thi can reset formBook
  resetForm()
}
function updateBook() {
  listSach.value[idUpdate.value] = { ...formBook.value } // Cap nhat thong tin sach
  resetForm()
  idUpdate.value = -1 // Reset idUpdate
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
