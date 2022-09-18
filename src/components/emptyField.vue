<template>
  <div
    class="field border-l-red-600"
    :style="{
      'background-image': 'url(' + fieldImg + ')',
      'background-repeat': 'no-repeat',
      'background-position': 'center',
      'background-size': '60%',
    }"
    :class="{
      filled: fieldImg,
      empty: !fieldImg,
      'border-l-2': fieldState === 'right' || fieldState === 'wrong',
      'border-green-600': fieldState === 'right',
      'border-red-600': fieldState === 'wrong',
    }"
  >
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";

export default defineComponent({
  props: {
    fieldImg: String,
    fieldState: String,
  },
  setup(props) {
    const getBorderStyle = (): string => {
      let borderStyle: string = "";
      if (props.fieldState === "right") {
        borderStyle = "solid";
      }

      return borderStyle;
    };
  },
});
</script>

<style>
.field {
  border-radius: 12px;
}
.empty {
  background-color: rgba(242, 242, 242, 1);
  border: 1px dashed #b0b2c1;
}
.filled {
  background: #ffffff;
  box-shadow: 0px 4px 4px rgba(12, 110, 214, 0.16);
}
</style>
