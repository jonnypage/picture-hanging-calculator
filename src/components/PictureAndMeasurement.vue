<template>
  <Picture :value="pictureWidth" />
  <PictureToPicture :value="spaceBetweenPictures" />
</template>

<script>
import Picture from "./Picture";
import PictureToPicture from "./measurements/PictureToPicture";
export default {
  name: "PictureAndMeasurement",
  components: {
    Picture,
    PictureToPicture,
  },
  props: {
    pictureWidth: Number,
    spaceBetweenPictures: Number,
    unit: {
      default: "mm",
      type: String,
    },
  },
};
</script>