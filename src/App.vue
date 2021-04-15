<template>
  <div class="container">
    <Header />
    <Measurements
      :initialData="{ wallWidth, pictureCount, pictureWidth }"
      @wall-width="setWallWidth"
      @picture-count="setPictureCount"
      @picture-width="setPictureWidth"
    />
    <div>
      <div>
        <div>Space Between Pictures: {{ spaceBetweenPictures }} cm</div>
        <div>
          Space Between Picture centers: {{ spaceBetweenPictureCenters }} cm
        </div>
        <div>
          Space From Wall To First Picture Center:
          {{ spaceFromWallToFirstPictureCenter }} cm
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import Header from "./components/Header";
import Measurements from "./components/Measurements";
export default {
  name: "App",
  components: {
    Header,
    Measurements,
  },
  methods: {
    setWallWidth(width) {
      this.wallWidth = width;
    },
    setPictureCount(count) {
      this.pictureCount = count;
    },
    setPictureWidth(width) {
      this.pictureWidth = width;
    },
  },
  data() {
    return {
      wallWidth: 203,
      pictureCount: 3,
      pictureWidth: 33.5,
      pictures: [{ pictureWidth: 0 }],
    };
  },
  computed: {
    spaceBetweenPictures: function () {
      //console.log("spaceBetweenPictures", this.wallWidth, this.pictureCount);
      const value =
        (this.wallWidth - this.pictureCount * this.pictureWidth) /
        (this.pictureCount + 1);

      return Math.round(value * 100) / 100;
    },
    spaceBetweenPictureCenters: function () {
      // console.log(
      //   "spaceBetweenPictureCenters",
      //   this.spaceBetweenPictures,
      //   this.pictureWidth
      // );
      const value = (this.spaceBetweenPictures + this.pictureWidth).toFixed(2);
      return Math.round(value * 100) / 100;
    },
    spaceFromWallToFirstPictureCenter: function () {
      // console.log(
      //   "spaceFromWallToFirstPictureCenter",
      //   this.spaceBetweenPictures,
      //   this.pictureWidth
      // );
      const value = (this.spaceBetweenPictures + this.pictureWidth / 2).toFixed(
        2
      );
      return Math.round(value * 100) / 100;
    },
  },
};
</script>

<style>
html {
  box-sizing: border-box;
}
*,
*:before,
*:after {
  box-sizing: inherit;
}
body {
  font-family: --apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Oxygen,
    Ubuntu, Cantarell, "Open Sans", "Helvetica Neue", sans-serif;
  margin: 0;
  padding: 0;
  overflow: hidden;
}
.container {
  display: flex;
  flex-direction: column;
  width: 100%;
}
</style>