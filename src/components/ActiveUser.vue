<template>
  <div>
    <li>
      <ul>
        <li>
          <h2>NAME: {{ userName }}</h2>
        </li>

        <li>
          <h3>AGE: {{ userAge }} Year</h3>
        </li>
      </ul>
    </li>
  </div>
</template>
<script>
export default {
  props: ["userName", "userAge"],
};
</script>
<style scoped>
li {
  list-style: none;
}
ul {
  border: 2px solid black;
  margin-bottom: 1rem;
}
</style>
