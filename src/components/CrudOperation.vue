<template>
  <div>
    <input type="text" v-model="search" placeholder="search" />
    <input type="text" placeholder="Add" v-model="inp" />
    <button @click="add">Add</button>

    <ul>
      <li v-for="(item, index) in filteredSearch" :key="index">
        {{ item }} <button @click="removeItem(index)">X</button
        ><button @click="editItem(index)">edit</button>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  data() {
    return {
      inp: "",
      data: [],
      edit: null,
      search: "",
    };
  },
  created() {
    this.data = ["saqeb"];
  },
  
  methods: {
    add() {
      if (this.edit === null) {
        this.data.push(this.inp);
        this.inp = "";
      } else {
        this.data[this.edit] = this.inp;
        this.edit = null;
        this.inp = "";
      }
    },
    removeItem(ind) {
      this.data.splice(ind, 1);
    },
    editItem(ind) {
      this.inp = this.data[ind];
      this.edit = this.inp;
      this.data.filter((ele) => {
        if (this.data.indexOf(ele) === ind) {
          this.inp = ele;
        }
      });
      this.edit = ind;
    },
  },
  computed: {
    filteredSearch() {
      return this.data.filter((item) => {
        return item.toLowerCase().includes(this.search.toLowerCase());
      });
    },
  },
};
</script>

<style scoped></style>
