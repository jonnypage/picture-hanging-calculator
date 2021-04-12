<template>
  <div>
    <div>
      <label for="wallWidth">Wall Width</label>
      <input
        type="number"
        id="wallWidth"
        name="wallWidth"
        v-model.number="wallWidth"
        v-on:change="computeWall"
      />
    </div>
    <div>
      <label for="pictureCount">Picture Count</label>
      <input
        type="number"
        id="pictureCount"
        name="pictureCount"
        v-model.number="pictureCount"
        v-on:change="computeWall"
      />
    </div>
    <div>
      <label for="pictureWidth">Picture Width</label>
      <input
        type="number"
        id="pictureWidth"
        name="pictureWidth"
        v-model.number="pictureWidth"
        v-on:change="computeWall"
      />
    </div>
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
</template>

<script>
export default {
  name: "App",
  components: {},
  methods: {
    computeWall() {
      this.spaceBetweenPictures =
        (this.wallWidth - this.pictureCount * this.pictureWidth) /
        (this.pictureCount + 1);
      this.spaceBetweenPictureCenters =
        this.spaceBetweenPictures + this.pictureWidth;
      this.spaceFromWallToFirstPictureCenter =
        this.spaceBetweenPictures + this.pictureWidth / 2;
    },
  },
  data() {
    return {
      wallWidth: 203,
      spaceBetweenPictures: 0,
      spaceBetweenPictureCenters: 0,
      spaceFromWallToFirstPictureCenter: 0,
      spaceToWall: 0,
      pictureCount: 3,
      pictureWidth: 33.5,
      pictures: [{ pictureWidth: 0 }],
    };
  },
  computed: {},
};
</script>

<style>
</style>