<template>
  <div
    class="empty"
    :style="{
      'background-image': 'url(' + fieldImg + ')',
      'background-repeat': 'no-repeat',
      'background-position': 'center',
      'background-size': '60%',
    }"
    :class="{filled: fieldImg}"
  ></div>
</template>

<script lang="ts">
import { defineComponent } from "vue";

export default defineComponent({
  props: {
    fieldImg: String,
  },
  setup() {},
});
/* 
style="background-image: url(require('@/assets/images/songs.svg'))"
:style="{
  backgroundimage: url(`${this.fieldImg}`),
  backgroundrepeat: no-repeat,
  backgroundposition: center,
  backgroundsize: contain,
}" */
</script>

<style>
.empty {
  height: 280px;
  background-color: rgba(242, 242, 242, 1);
  border: 1px dashed #b0b2c1;
  border-radius: 12px;
}
.filled{
  background: #ffffff;
  box-shadow: 0px 4px 4px rgba(12, 110, 214, 0.16);
  border: none;
}
</style>
