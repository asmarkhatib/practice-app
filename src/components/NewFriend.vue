<template>
  <div>
    <div>
      <label for="name">Name: </label>
      <input type="text" id="name" v-model="enteredName" />
    </div>
    <div>
      <label for="phone">Phone: </label>
      <input type="text" id="phone" v-model="enteredPhone" />
    </div>
    <div>
      <label for="email">E-Mail: </label>
      <input type="email" id="email" v-model="enteredEmail" />
    </div>
    <div>
      <button @click="addContacts">Add Contact</button>
    </div>
  </div>
</template>
<script>
export default {
  data() {
    return {
      enteredName: "",
      enteredPhone: "",
      enteredEmail: "",
    };
  },
  emits: [],
  methods: {
    addContacts() {
      this.$emit(
        "add-contact",
        this.enteredName,
        this.enteredPhone,
        this.enteredEmail
      );
    },
  },
};
</script>
<style scoped></style>
