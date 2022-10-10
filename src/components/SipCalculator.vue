<template>
  <div>
    <label for="select">Select: </label>
    <select id="select" v-model="selected">
      <option value="month">Monthly</option>
      <option value="year">Yearly</option>
    </select>
    <p>
      <label for="money">Monthly Investment Amount*:</label>
      <input
        type="number"
        id="money"
        placeholder="Ex:1000"
        required
        v-model.number="rupee"
      />
    </p>
    <p>
      <label for="rate">Expected rate of return (P.A)*:</label>
      <input
        type="number"
        id="rate"
        placeholder="Ex:12%"
        required
        v-model.number="interest"
      />
    </p>
    <p>
      <label for="month">Tenure (in years)*:</label>
      <input
        type="number"
        id="month"
        placeholder="Ex:10"
        required
        v-model.number="year"
      />
    </p>
    <section>
      <button @click="totalEarning">Plan My Wealth</button>
      <h4 v-html="result"></h4>
    </section>
  </div>
</template>
<script>
export default {
  data() {
    return {
      selected: "",
      rupee: null,
      year: null,
      interest: null,
      result: "",
    };
  },
  methods: {
    totalEarning() {
      let total = 0;
      let corpus = [];
      let updated = this.rupee;
      if (this.selected === "month") {
        let ratePerMonth = this.interest / 12;

        for (let i = 1; i <= this.year * 12; i++) {
          updated = (ratePerMonth / 100) * updated + updated;
          corpus.push(updated);
        }

        corpus.forEach((ele) => (total += ele));

        this.result = `<p> Your future value ${total.toFixed(2)} </p>
        <p>Your total earning ${
          total - this.rupee * (this.year * 12).toFixed(2)
        }</p>
        <p>Total amount deposited ${this.rupee * (this.year * 12)}</p>`;
      } else {
        for (let i = 1; i <= this.year; i++) {
          updated = (this.interest / 100) * updated + updated;
          corpus.push(updated);
        }
        let totalInvest = this.rupee * this.year;
        let totalIntrsetEarn = total - totalInvest;
        corpus.forEach((ele) => (total += ele));
        this.result = `<p> Your future value ${total.toFixed(2)} </p>
        <p>Your total earning ${totalIntrsetEarn.toFixed(2)}</p>
        <p>Total amount deposited ${totalInvest}</p>`;
      }
    },
    // tInvest() {
    //   this.totalInvest = this.rupee * (this.year * 12);
    //   console.log("totalInvest =>", this.totalInvest);
    //   return this.totalInvest;
    // },
    // earnI() {
    //   this.earnIntrest = this.tEarning - this.totalInvest;
    //   console.log("earnIntrset =>", this.earnIntrest);
    //   return this.earnIntrest;
    // },
    // result() {
    //   this.tEarning = "Your Future Value:" + "" + this.totalEarning();
    //   this.earnIntrest = "Total Earnings:" + "" + this.earnI();
    //   this.totalInvest = "Total Amount Deposited:" + "" + this.tInvest();
    // },
  },
};
</script>
<style scoped></style>
