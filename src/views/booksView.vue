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
    <div class="bookworld__container">
      <header class="bookworld__title">В мире книг</header>
      <main class="bookworld__content">
        <section class="bookworld__cards">
          <book-card
            @dragstart="onDragStart($event, book)"
            class="book__card"
            v-for="book in books"
            :key="book.id"
            :book="book"
          ></book-card>
        </section>
        <section class="bookworld__answers">
          <div class="book__fields-titles">
            <div class="folklor__fields-title">Жанры фольклора</div>
            <div class="nofolklor__fields-title">
              Не являются жанрами фольклора
            </div>
          </div>
          <div class="book__fields">
            <empty-field
              class="book__field"
              v-for="field in bookFields"
              :key="field.id"
              :fieldImg="field.imgSrc"
              :fieldState="field.state"
              @drop="onDrop($event, field)"
              @dragenter.prevent
              @dragover.prevent
            ></empty-field>
          </div>
        </section>
      </main>
      <my-button class="bookworld__check" @click="checkAnswers"
        >Проверить</my-button
      >
    </div>
  </main>
</template>
<script lang="ts">
import BookCard from "@/components/bookCard.vue";
import myButton from "../components/UI/myButton.vue";
import EmptyField from "@/components/emptyField.vue";
import { defineComponent, ref } from "vue";
export default defineComponent({
  components: { myButton, BookCard, EmptyField },
  setup() {
    type Tbook = {
      id: number;
      name: string;
      type: string;
      imgSrc: string;
    };
    type Tfield = {
      id: number;
      imgSrc: string;
      ownType: string;
      innerType: string;
      state: string;
    };
    const books = ref<Tbook[]>([
      {
        id: 1,
        name: "folkTales",
        type: "folklor",
        imgSrc: require("@/assets/images/tales.svg"),
      },
      {
        id: 2,
        name: "folkSongs",
        type: "folklor",
        imgSrc: require("@/assets/images/songs.svg"),
      },
      {
        id: 3,
        name: "piterPan",
        type: "nofolklor",
        imgSrc: require("@/assets/images/piterPan.svg"),
      },
      {
        id: 4,
        name: "proverbs",
        type: "folklor",
        imgSrc: require("@/assets/images/proverbs.svg"),
      },
      {
        id: 5,
        name: "motherland",
        type: "nofolklor",
        imgSrc: require("@/assets/images/motherland.svg"),
      },
      {
        id: 6,
        type: "nofolklor",
        name: "childhood",
        imgSrc: require("@/assets/images/childhood.svg"),
      },
    ]);
    const bookFields = ref<Tfield[]>([
      {
        id: 1,
        imgSrc: "",
        ownType: "folklor",
        innerType: "",
        state: "neutral",
      },
      {
        id: 2,
        imgSrc: "",
        ownType: "folklor",
        innerType: "",
        state: "neutral",
      },
      {
        id: 3,
        imgSrc: "",
        ownType: "folklor",
        innerType: "",
        state: "neutral",
      },
      {
        id: 4,
        imgSrc: "",
        ownType: "folklor",
        innerType: "",
        state: "neutral",
      },
      {
        id: 5,
        imgSrc: "",
        ownType: "folklor",
        innerType: "",
        state: "neutral",
      },
      {
        id: 6,
        imgSrc: "",
        ownType: "folklor",
        innerType: "",
        state: "neutral",
      },
      {
        id: 7,
        imgSrc: "",
        ownType: "nofolklor",
        innerType: "",
        state: "neutral",
      },
      {
        id: 8,
        imgSrc: "",
        ownType: "nofolklor",
        innerType: "",
        state: "neutral",
      },
      {
        id: 9,
        imgSrc: "",
        ownType: "nofolklor",
        innerType: "",
        state: "neutral",
      },
      {
        id: 10,
        imgSrc: "",
        ownType: "nofolklor",
        innerType: "",
        state: "neutral",
      },
      {
        id: 11,
        imgSrc: "",
        ownType: "nofolklor",
        innerType: "",
        state: "neutral",
      },
      {
        id: 12,
        imgSrc: "",
        ownType: "nofolklor",
        innerType: "",
        state: "neutral",
      },
    ]);

    const onDragStart = (event: DragEvent, book: Tbook) => {
      event.dataTransfer!.dropEffect = "move";
      event.dataTransfer!.effectAllowed = "move";
      event.dataTransfer!.setData("type", book.type);
      event.dataTransfer!.setData("imgSrc", book.imgSrc);
    };
    const onDrop = (event: DragEvent, field: Tfield) => {
      const bookImg = event.dataTransfer!.getData("imgSrc");
      const bookType = event.dataTransfer!.getData("type");
      const currentField = bookFields.value.find(
        (item: Tfield) => item.id === field.id
      );
      currentField!.imgSrc = bookImg;
      currentField!.innerType = bookType;
    };
    const checkAnswers = (): void => {
      for (let i = 0; i <= bookFields.value.length-1; i++) {
        let currentItem = bookFields.value[i];
        if (currentItem.innerType !== "") {
          if (currentItem.ownType === currentItem.innerType) {
            currentItem.state = "right";
          } else if (currentItem.ownType !== currentItem.innerType) {
            currentItem.state = "wrong";
          }
          
        }
      }
    };
    return {
      books,
      bookFields,
      onDragStart,
      onDrop,
      checkAnswers,
    };
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
.bookworld__container {
  width: 95%;
  margin: auto;
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
  filter: drop-shadow(0px 4px 4px rgba(0, 0, 0, 0.25))
    drop-shadow(0px 4px 4px rgba(0, 0, 0, 0.25));
}
.bookworld__content {
  display: flex;
}
.bookworld__cards {
  width: 50%;
  flex-wrap: wrap;
  display: flex;
  margin-top: 89px;
  max-height: 865px;
  justify-content: space-around;
}
.book__card {
  margin-bottom: 12px;
}
.bookworld__answers {
  width: 50%;
}
.book__fields {
  display: grid;
  justify-content: center;
  grid-template-columns: repeat(2, 280px);
  grid-template-rows: repeat(6, 280px);
  grid-auto-flow: column;
  grid-row-gap: 12px;
  grid-column-gap: 48px;
}
.book__field {
}
.book__fields-titles {
  display: grid;
  grid-template-columns: repeat(2, 280px);
  grid-column-gap: 48px;
  justify-content: center;
}
.folklor__fields-title,
.nofolklor__fields-title {
  font-weight: 600;
  font-size: 18px;
  line-height: 22px;
  text-align: center;
  color: #183b59;
  height: 44px;
  margin-bottom: 20px;
  margin-top: 25px;
  width: 280px;
}

.bookworld__check {
  padding: 12px 52px;
  margin-top: 32px;
  margin-bottom: 32px;
  display: flex;
  align-items: left;
}
</style>
