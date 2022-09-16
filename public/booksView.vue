<template>
  <nav class="navbar">
    <div class="navbar__back" @click="this.$router.push('/')">
      <my-button class="navbar__back-button"
        ><img src="@/assets/images/arrow.png" class="backarrow" alt=""
      /></my-button>
      <p class="navbar__back-word">Назад</p>
    </div>
  </nav>
  <main class="bookworld">
    <div class="container">
      <header class="bookworld__title">В мире книг</header>
      <main class="bookworld__content">
        <section class="bookworld__cards">
          <book-card
            class="book__card"
            v-for="book in books"
            :key="book.id"
            :book="book"
          ></book-card>
        </section>
        <section class="bookworld__answers">
          <div class="folklor__fields">
            <div class="folklor__fields-title">Жанры фольклора</div>
            <empty-field v-for="book in books" :key="book.id"></empty-field>
          </div>
          <div class="nofolklor__fields">
            <div class="folklor__fields-title">Не являются жанрами фольклора</div>
          </div>
        </section>
      </main>
    </div>
  </main>
</template>
<script lang="ts">
import BookCard from "@/components/bookCard.vue";
import myButton from "../src/components/UI/myButton.vue";
import EmptyField from "@/components/emptyField.vue";
import { defineComponent, reactive, ref, toRefs } from "vue";
export default defineComponent({
  components: { myButton, BookCard, EmptyField },
  setup() {
    const books = ref([
      {
        id: 1,
        name: "folkTales",
        isFolklor: true,
        imgSrc: require("@/assets/images/tales.svg"),
      },
      {
        id: 2,
        name: "folkSongs",
        isFolklor: true,
        imgSrc: require("@/assets/images/songs.svg"),
      },
      {
        id: 3,
        name: "piterPan",
        isFolklor: false,
        imgSrc: require("@/assets/images/piterPan.svg"),
      },
      {
        id: 4,
        name: "proverbs",
        isFolklor: true,
        imgSrc: require("@/assets/images/proverbs.svg"),
      },
      {
        id: 5,
        name: "motherland",
        isFolklor: false,
        imgSrc: require("@/assets/images/motherland.svg"),
      },
      {
        id: 6,
        name: "childhood",
        isFolklor: false,
        imgSrc: require("@/assets/images/childhood.svg"),
      },
    ]);
    return { books };
  },
});
</script>

<style>
.navbar {
  height: 80px;
  box-shadow: 0px 4px 4px rgba(12, 110, 214, 0.16);
  border-radius: 8px;
}
.navbar__back {
  display: flex;
  align-items: center;
  cursor: pointer;
}
.navbar__back-button {
  padding: 8px;
}
.backarrow {
  width: 14px;
  height: 14px;
}
.navbar__back-word {
  color: rgba(139, 215, 75, 1);
  margin-left: 8px;
}
.bookworld {
}
.container {
  width: 95%;
}
.bookworld__title {
  background: linear-gradient(90deg, #3f8cff 0.06%, #60b9a6 99.94%);
  height: 128px;
  border-radius: 24px;
  font-size: 40px;
  color: white;
  font-weight: 700;
  display: flex;
  align-items: center;
  justify-content: center;
}
.bookworld__content {
  display: flex;
}
.bookworld__cards {
  width: 50%;
  flex-wrap: wrap;
  display: flex;
  margin-top: 89px;
}
.book__card {
  margin-bottom: 12px;
}
</style>
