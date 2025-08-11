<template>
  <section class="container">
    <!-- Form Sach Component  -->
    <form>
      <div class="mb-3">
        <label for="exampleFormControlInput1" class="form-label">Tên</label>
        <input type="text" class="form-control" v-model="book.ten" />
      </div>
      <div class="mb-3">
        <label for="exampleFormControlInput1" class="form-label">Loại</label>
        <select class="form-select" aria-label="Default select example" v-model="book.loai">
          <option selected>Open this select menu</option>
          <option value="Loai 1">Loai 1</option>
          <option value="Loai 2">Loai 2</option>
          <option value="Loai 3">Loai 3</option>
        </select>
      </div>
      <div class="mb-3">
        <label for="exampleFormControlInput1" class="form-label">Tác giả</label>
        <input type="text" class="form-control" v-model="book.tacGia" />
      </div>
      <div class="mb-3">
        <label for="exampleFormControlInput1" class="form-label">Giá</label>
        <input type="text" class="form-control" v-model="book.gia" />
      </div>
    </form>
  </section>
</template>

<script setup>
// goi model tu component cha
defineModel('book', {
  // arrow function
  default: () => ({
    // liet ke cac thuoc tinh cua sach
    ten: '',
    loai: '',
    tacGia: '',
    gia: 0,
  }),
})
</script>

<style scoped></style>
