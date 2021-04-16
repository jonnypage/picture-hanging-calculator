<template>
  <div class="wall-visualization">
    <div class="ceiling"></div>
    <div class="wall">
      <div class="doorway doorway--left"></div>
      <div class="wall-center-area">
        <div class="wall-width">{{ wallWidth }}{{ unit }}</div>
        <div class="pictures">
          <WallToPicture :value="spaceBetweenPictures" />
          <PictureAndMeasurement
            v-for="n in pictureCount - 1"
            :key="n"
            :pictureWidth="pictureWidth"
            :spaceBetweenPictures="spaceBetweenPictures"
          />
          <Picture :value="pictureWidth" />
          <WallToPicture :value="spaceBetweenPictures" />
        </div>
        <div class="floor"></div>
      </div>
      <div class="doorway doorway--right"></div>
    </div>
  </div>
</template>

<script>
import Picture from "./Picture";
import PictureAndMeasurement from "./PictureAndMeasurement";
import WallToPicture from "./measurements/WallToPicture";
import ceilingImage from "/public/images/ceiling-line.svg";
import doorwayLeft from "/public/images/left-door.png";
import doorwayRight from "/public/images/right-door.png";
export default {
  name: "WallVisualization",
  components: {
    Picture,

    WallToPicture,
    PictureAndMeasurement,
  },
  props: {
    wallWidth: Number,
    pictureCount: Number,
    pictureWidth: Number,
    spaceBetweenPictures: Number,
    spaceBetweenPictureCenters: Number,
    spaceFromWallToFirstPictureCenter: Number,
    unit: {
      default: "mm",
      type: String,
    },
  },
  data: function () {
    return {
      ceilingImage,
      doorwayLeft,
      doorwayRight,
    };
  },
};
</script>
<style>
.wall-visualization {
  display: flex;
  align-content: center;
  flex-direction: column;
  width: 100%;
}
.ceiling,
.floor {
  width: 98%;
  margin: 0 1%;
  height: 20px;
}
.ceiling {
  background-image: url("~./../../public/images/ceiling-line.svg");
  background-size: auto;
  background-repeat: no-repeat;
  margin-bottom: 40px;
}
.floor {
  background-image: url("~./../../public/images/ceiling-line.svg");
  background-size: auto;
  background-repeat: no-repeat;
}
.wall {
  display: flex;
  flex-direction: row;
  width: 100%;
  height: 20vw;
  justify-content: space-between;
}
.wall .doorway {
  flex: 1;
  width: 20vw;
  height: 20vw;
}
.wall .doorway.doorway--left {
  background-image: url("~./../../public/images/left-door.svg");
  background-position: right bottom;
  background-size: cover;
}
.wall .doorway.doorway--right {
  background-image: url("~./../../public/images/right-door.svg");
  background-position: left bottom;
  background-size: cover;
}
.wall-center-area {
  flex: 4;
  display: flex;
  height: 20vw;
  flex-direction: column;
}
.wall-width {
  display: flex;
  align-items: center;
  justify-content: center;
}
.pictures {
  display: flex;
  flex-direction: row;
  width: 100%;
  height: 100%;
  justify-content: space-between;
  align-items: center;
}
.pictures .measurement {
  flex: 1;
  display: flex;
  align-items: center;
  justify-content: center;
}
.pictures .picture {
  height: 6vw;
  flex: 1;
  display: flex;
  align-items: center;
  justify-content: center;
  background-image: url("~./../../public/images/picture-1.svg");
  background-position: center;
  background-size: contain;
  background-repeat: no-repeat;
}
</style>

