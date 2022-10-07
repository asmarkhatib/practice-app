<template>
  <div>
    <!-- <TitleComp /> -->
    <input type="text" placeholder="First Name" v-model="fName" /> <br /><br />
    <input type="text" placeholder="Second Name" v-model="sName" /><br /><br />
    <label for="source">Select Source</label>
    <select name="" id="source" v-model="source">
      <option v-for="(station, index) in stations" :key="index">
        {{ station }}
      </option></select
    ><br /><br />
    <label for="destination">Select Destination</label>
    <select name="" id="destination" v-model="destination">
      <option v-for="(tation, index) in stations" v-bind:key="index">
        {{ tation }}
      </option></select
    ><br /><br />

    <input
      type="number"
      placeholder="Number Of passengers"
      v-model="passengers"
    />
    <button @click="printTicket">Generate Ticket</button>
    <div v-if="print">
      <h3>Hello Mr.{{ fName }} {{ sName }} We Wish You Happy Journey</h3>
      <h4>Here is the details of your travel</h4>
      <p>
        The Cost for source {{ source }} to destination {{ destination }} for
        {{ passengers }} person/people will be {{ cost }}
      </p>
    </div>
  </div>
</template>

<script>
// import TitleComp from "./components/TitleComp.vue";
export default {
  components: {
    // TitleComp,
  },
  data() {
    return {
      fName: "",
      sName: "",
      source: "",
      destination: "",
      passengers: null,
      stations: [
        "Aurangabad",
        "Jalna",
        "Partur",
        "Selu",
        "Manwat Road",
        "Parbhani",
        "Purna",
        "Nanded",
      ],
      cost: 0,
      print: false,
    };
  },
  watch: {
    source(val) {
      this.stations.splice(0, this.stations.indexOf(val) + 1);
    },
  },
  methods: {
    printTicket() {
      this.print = true;
      let count = 0;
      for (
        let i = this.stations.indexOf(this.source);
        i < this.stations.indexOf(this.destination);
        i++
      ) {
        count++;
      }
      this.cost = count * 50 * this.passengers;
    },
  },
};
</script>

<style scoped></style>
