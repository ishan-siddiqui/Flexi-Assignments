<template>
  <div class="container">
    <h1 class="title">Currency Converter</h1>
    <form>
      <div class="form-group">
        <label for="dollar">Dollar:</label>
        <input type="number" class="form-control" id="dollar" v-model="dollar" @input="convertToINR" />
      </div>
      <div class="form-group">
        <label for="inr">INR:</label>
        <input type="number" class="form-control" id="inr" v-model="inr" @input="convertToDollar" />
      </div>
    </form>
  </div>
</template>

<script>
export default {
  data() {
    return {
      dollar: null,
      inr: null,
      exchangeRate: 73.93, // 1 USD = 73.93 INR (as of Sep 2021)
    };
  },
  methods: {
    convertToINR() {
      if (this.dollar) {
        this.inr = (this.dollar * this.exchangeRate).toFixed(2);
      } else {
        this.inr = null;
      }
    },
    convertToDollar() {
      if (this.inr) {
        this.dollar = (this.inr / this.exchangeRate).toFixed(2);
      } else {
        this.dollar = null;
      }
    },
  },
};
</script>

<style>
.container {
  max-width: 600px;
  margin: 0 auto;
}

.title {
  text-align: center;
}

.form-group {
  margin-bottom: 20px;
}

.form-control {
  padding: 10px;
  border: 1px solid #ccc;
  border-radius: 4px;
  width: 100%;
  font-size: 16px;
}
</style>
