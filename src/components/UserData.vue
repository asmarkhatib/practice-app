<template>
  <div>
    <label for="">Name: </label>
    <input type="text" v-model="userName" />
  </div>
  <div>
    <label for="">Age: </label>
    <input type="text" v-model="age" />
  </div>
  <div>
    <button @click="submitData">Submit</button>
  </div>
</template>
<script>
export default {
  data() {
    return {
      userName: "",
      age: "",
    };
  },
  methods: {
    submitData() {
      this.$emit("adduser-data", this.userName, this.age);
    },
  },
};
</script>
<style scoped></style>
