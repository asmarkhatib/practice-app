<template>
  <div>
    <li>
      <h2>{{ name }}</h2>
      <button @click="showDetails">
        {{ listIsVisible ? "Hide" : "Show" }} Details
      </button>
      <ul v-if="listIsVisible">
        <li>{{ phone }}</li>
        <li>{{ email }}</li>
      </ul>
    </li>
  </div>
</template>
<script>
export default {
  data() {
    return {
      listIsVisible: false,
    };
  },
  props: {
    name: {
      type: String,
      requried: true,
    },
    phone: {
      type: String,
      requried: true,
    },
    email: {
      type: String,
      requried: true,
    },
  },
  methods: {
    showDetails() {
      this.listIsVisible = !this.listIsVisible;
    },
  },
};
</script>
<style scoped></style>
