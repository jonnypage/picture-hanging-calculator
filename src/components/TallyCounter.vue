<template>
  <div class="tally-counter">
    <label>{{ title }}</label>
    <div>
      <i @click="onSubtractClick" class="fas fa-minus-square"></i>
      {{ count }}
      <i @click="onAddClick" class="fas fa-plus-square"></i>
    </div>
  </div>
</template>

<script>
export default {
  name: "TallyCounter",
  props: {
    title: String,
    initialValue: Number,
  },
  data() {
    return {
      count: 0,
    };
  },
  created() {
    this.count = this.initialValue;
  },
  methods: {
    onSubtractClick() {
      if (this.count >= 2) {
        this.count = this.count - 1;
        this.$emit("tally-change", this.count);
      }
    },
    onAddClick() {
      this.count = this.count + 1;
      this.$emit("tally-change", this.count);
    },
  },
  emits: {
    "tally-change": Number,
  },
};
</script>
<style scoped>
.tally-counter {
  display: flex;
  flex-direction: column;
}
label {
  font-weight: bold;
}
i:hover {
  cursor: pointer;
}
</style>