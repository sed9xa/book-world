<template>
  <div class="container">
    <h1 class="book__title">В мире книг</h1>
    <article class="book__instruction">
      <h3 class="instruction-title">Инструкция:</h3>
      <p class="instruction-text">
        Распредели книги, ориентируясь на названия, по соответствующим рубрикам
        таблицы: «Жанры фольклора», «Не являются жанрами фольклора».
      </p>
    </article>
    <my-button @click="this.$router.push('/books')" class="book__btn"
      >Продолжить</my-button
    >
  </div>
</template>

<script lang="ts">
import myButton from "@/components/UI/myButton.vue";
import { defineComponent } from "vue";

export default defineComponent({
  components: {
    myButton,
  },
});
</script>

<style>
.container {
  width: 60%;
  margin: auto;
}
.book__title {
  margin-top: 60px;
  text-align: left;
  color: rgba(139, 215, 75, 1);
  font-size: 40px;
  font-weight: 700;
  margin-bottom: 36px;
}
.book__instruction {
  text-align: left;
  background-color: rgba(0, 0, 0, 0.05);
  margin-bottom: 36px;
  padding: 22px 36px;
  border-radius: 0px 0px 20px 20px;
  border-top: rgba(139, 215, 75, 1) solid 2px;
}
.instruction-title {
  color: rgba(24, 59, 89, 1);
  font-weight: 700;
  font-size: 25px;
  margin-bottom: 12px;
}
.instruction-text {
  color: rgba(24, 59, 89, 1);
}
.book__btn {
  display: flex;
  align-self: left;
  padding: 12px 52px;
}
</style>
