<template>
  <div class="container">
    <Header />
    <div class="measurement-input">
      <TextInput
        title="Width of the wall"
        @input-change="setWallWidth"
        :initialValue="wallWidth"
      />
      <TallyCounter
        title="Number of Pictures"
        @tally-change="setPictureCount"
        :initialValue="pictureCount"
      />
      <TextInput
        title="Width of the picture"
        @input-change="setPictureWidth"
        :initialValue="pictureWidth"
      />
    </div>
    <!-- <div>
      <div>
        <div>Space Between Pictures: {{ spaceBetweenPictures }} cm</div>
        <div>
          Space Between Picture centers: {{ spaceBetweenPictureCenters }} cm
        </div>
        <div>
          Space From Wall To First Picture Center:
          {{ spaceFromWallToFirstPictureCenter }} cm
        </div>
        <div v-show="spaceBetweenPictures ? false : true">
          Opps, the pictures overlap!
        </div>
      </div>
    </div> -->
    <WallVisualization
      :wallWidth="wallWidth"
      :pictureCount="pictureCount"
      :pictureWidth="pictureWidth"
      :spaceBetweenPictures="spaceBetweenPictures"
      :spaceBetweenPictureCenters="spaceBetweenPictureCenters"
      :spaceFromWallToFirstPictureCenter="spaceFromWallToFirstPictureCenter"
    />
  </div>
</template>

<script>
import Header from "./components/Header";
import TextInput from "./components/TextInput";
import TallyCounter from "./components/TallyCounter";
import WallVisualization from "./components/WallVisualization";
export default {
  name: "App",
  components: {
    Header,
    TextInput,
    TallyCounter,
    WallVisualization,
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
      picturesOverlap: false,
    };
  },
  computed: {
    spaceBetweenPictures: function () {
      const value =
        (this.wallWidth - this.pictureCount * this.pictureWidth) /
        (this.pictureCount + 1);

      if (value <= 0) {
        return 0;
      }
      return Math.round(value * 100) / 100;
    },
    spaceBetweenPictureCenters: function () {
      const value = this.spaceBetweenPictures + this.pictureWidth;

      return Math.round(value * 100) / 100;
    },
    spaceFromWallToFirstPictureCenter: function () {
      const value = this.spaceBetweenPictures + this.pictureWidth / 2;

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
.measurement-input {
  display: flex;
  align-items: center;
  justify-content: space-around;
  margin-bottom: 20px;
}
</style>