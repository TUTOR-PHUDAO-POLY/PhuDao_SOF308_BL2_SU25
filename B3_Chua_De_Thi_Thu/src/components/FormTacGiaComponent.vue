<template>
  <section class="container">
    <form>
      <div class="mb-3">
        <label for="exampleFormControlInput1" class="form-label">Tên</label>
        <input type="text" class="form-control" v-model="tacGia.ten" />
      </div>
      <div class="mb-3">
        <label for="exampleFormControlInput1" class="form-label">Giới tính</label>
        <div class="form-check">
          <input
            class="form-check-input"
            type="radio"
            name="flexRadioDefault"
            id="flexRadioDefault1"
            :value="true"
            v-model="tacGia.gioiTinh"
          />
          <!-- true & "true" -->
          <!-- true  khac "true"
          1.  "1" -->
          <label class="form-check-label" for="flexRadioDefault1"> Nam </label>
        </div>
        <div class="form-check">
          <input
            class="form-check-input"
            type="radio"
            name="flexRadioDefault"
            id="flexRadioDefault2"
            :value="false"
            v-model="tacGia.gioiTinh"
          />
          <label class="form-check-label" for="flexRadioDefault2"> Nữ</label>
        </div>
      </div>
      <div class="mb-3">
        <label for="exampleFormControlInput1" class="form-label">Địa chỉ</label>
        <input type="text" class="form-control" v-model="tacGia.diaChi" />
      </div>
      <div class="mb-3">
        <label for="exampleFormControlInput1" class="form-label">Tuổi</label>
        <input type="text" class="form-control" v-model="tacGia.tuoi" />
      </div>
    </form>
  </section>
</template>

<script setup>
defineModel('tacGia', {
  default: () => ({
    ten: '',
    gioiTinh: false,
    diaChi: '',
    tuoi: 0,
  }),
})
</script>

<style scoped></style>
