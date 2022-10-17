<template>
  <div>
    <new-friend @add-contact="submitContact"></new-friend>
    <ul>
      <friend-details
        v-for="(friend, index) in friends"
        :key="index"
        :name="friend.name"
        :phone="friend.phone"
        :email="friend.email"
      ></friend-details>
    </ul>
  </div>
</template>
<script>
import FriendDetails from "./FriendDetails.vue";
import NewFriend from "./NewFriend.vue";
export default {
  components: {
    FriendDetails,
    NewFriend,
  },
  data() {
    return {
      friends: [
        {
          name: "Asmar Khatib",
          phone: "839273 92839",
          email: "asmarkhaib@local.com",
        },
      ],
    };
  },
  methods: {
    submitContact(name, phone, email) {
      const newFriend = {
        name: name,
        phone: phone,
        email: email,
      };
      this.friends.push(newFriend);
    },
  },
};
</script>
