<template>
  <div class="text-input">
    <label>{{ title }}</label>
    <input type="text" v-model="inputValue" @input="onInput" />
  </div>
</template>

<script>
export default {
  name: "TextInput",
  props: {
    title: String,
    initialValue: Number,
  },
  data() {
    return {
      inputValue: 0,
    };
  },
  created() {
    this.inputValue = this.initialValue;
  },
  methods: {
    onInput(evt) {
      if (evt.target.value !== "") {
        this.$emit("input-change", parseInt(evt.target.value));
      }
    },
  },
  emits: {
    "input-change": Number,
  },
};
</script>
<style scoped>
.text-input {
  display: flex;
  flex-direction: column;
}
label {
  font-weight: bold;
}
</style>