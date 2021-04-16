<template>
  <div class="picture">{{ value }}{{ unit }}</div>
</template>

<script>
export default {
  name: "Picture",
  props: {
    value: Number,
    unit: {
      default: "mm",
      type: String,
    },
  },
  data() {
    return {
      pictureFrames: 4,
    };
  },
  computed: {
    pictureFrame: function () {
      let frame = Math.floor(Math.random() * this.pictureFrames) + 1;

      return frame;
    },
  },
};
</script>