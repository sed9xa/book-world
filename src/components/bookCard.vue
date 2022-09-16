<template>
  <div class="bookworld__card">
    <img
      class="bookworld__card-dots"
      src="../assets/images/dots.svg"
      alt="dots"
    />
    <img
      class="bookworld__card-img"
      :src="book.imgSrc"
      alt="Book-img"
    />

  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";

export default defineComponent({
  props: {
    book: Object,
  },
  setup() {},
});
</script>

<style>
.bookworld__card {
  display: flex;
  align-items: center;
  width: 285px;
  height: 280px;
  background: #ffffff;
  box-shadow: 0px 4px 4px rgba(12, 110, 214, 0.16);
  border-radius: 12px;
}
.bookworld__card-img {
}
.bookworld__card-dots {
  height: 15px;
  width: 9px;
  margin-right: 37px;
  margin-left: 17px;
}
</style>
