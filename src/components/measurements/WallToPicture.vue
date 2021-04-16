<template>
  <div class="measurement picture-picture">{{ value }}{{ unit }}</div>
</template>

<script>
export default {
  name: "PictureToPicture",
  props: {
    value: Number,
    unit: {
      default: "mm",
      type: String,
    },
  },
};
</script>