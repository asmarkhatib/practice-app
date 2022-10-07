<template>
  <div>
    <select v-model="selected">
      <option value="usd">USD</option>
      <option value="prk">PRK</option>
    </select>
    <input type="number" v-model="inr" placeholder="indian" />
    <input type="number" v-model="converted" :placeholder="selected" />
  </div>
</template>
<script>
export default {
  data() {
    return {
      // inr: null,
      selected: "",
    };
  },

  computed: {
    converted() {
      if (this.selected === "usd") {
        return this.inr * 0.012;
      } else {
        return this.inr * 2.71;
      }
    },
  },
};
</script>
<style scoped></style>
