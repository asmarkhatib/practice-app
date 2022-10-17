<template>
  <div>
    <ul>
      <active-user
        v-for="(data, index) in userData"
        :key="index"
        :user-name="data.name"
        :user-age="data.age"
      ></active-user>
    </ul>
    <user-data @adduser-data="addData"></user-data>
  </div>
</template>
<script>
import ActiveUser from "./ActiveUser.vue";
import UserData from "./UserData.vue";
export default {
  components: {
    ActiveUser,
    UserData,
  },
  data() {
    return {
      userData: [
        {
          name: "Asmar Khatib",
          age: 23,
        },
      ],
    };
  },
  methods: {
    addData(name, age) {
      const newUser = {
        name: name,
        age: age,
      };
      this.userData.push(newUser);
      // this.userData = newUser;
    },
  },
};
</script>
<style scoped></style>
