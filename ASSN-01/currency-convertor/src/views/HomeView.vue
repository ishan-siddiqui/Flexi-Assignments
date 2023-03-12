<template>
  <div>
    <form>
      <div>
        <label>Dollar value:</label>
        <input type="number" v-model="dollarValue" />
      </div>
      <div>
        <label>INR value:</label>
        <input type="number" v-model="inrValue" />
      </div>
      <button @click="convert">Convert</button>
    </form>
  </div>
</template>

<script>
export default {
  data() {
    return {
      dollarValue: null,
      inrValue: null,
      exchangeRate: 73.93, // 1 USD = 73.93 INR (as of Sep 2021)
    };
  },
  methods: {
    convert() {
      if (this.dollarValue) {
        this.inrValue = this.dollarValue * this.exchangeRate;
      } else if (this.inrValue) {
        this.dollarValue = this.inrValue / this.exchangeRate;
      }
    },
  },
};
</script>
