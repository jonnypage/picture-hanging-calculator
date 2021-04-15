<template>
  <div>
    <label for="wallWidth">Wall Width</label>
    <input
      type="number"
      id="wallWidth"
      name="wallWidth"
      v-model="wallWidth"
      @keyup="onWallWidth"
      @change="onWallWidth"
    />
  </div>
  <div>
    <label for="pictureCount">Picture Count</label>
    <input
      type="number"
      id="pictureCount"
      name="pictureCount"
      v-model="pictureCount"
      @change="onPictureCount"
    />
  </div>
  <div>
    <label for="pictureWidth">Picture Width</label>
    <input
      type="number"
      id="pictureWidth"
      name="pictureWidth"
      v-model="pictureWidth"
      @change="onPictureWidth"
    />
  </div>
</template>

<script>
export default {
  name: "Measurements",
  props: {
    initialData: Object,
  },
  data() {
    return {
      wallWidth: 0,
      pictureCount: 0,
      pictureWidth: 0,
    };
  },
  created() {
    this.wallWidth = this.initialData.wallWidth;
    this.pictureCount = this.initialData.pictureCount;
    this.pictureWidth = this.initialData.pictureWidth;
  },
  methods: {
    onWallWidth(evt) {
      this.$emit("wall-width", parseInt(evt.target.value));
    },
    onPictureCount(evt) {
      this.$emit("picture-count", parseInt(evt.target.value));
    },
    onPictureWidth(evt) {
      this.$emit("picture-width", parseInt(evt.target.value));
    },
  },
  emits: {
    "wall-width": Number,
    "picture-count": Number,
    "picture-width": Number,
  },
};
</script>