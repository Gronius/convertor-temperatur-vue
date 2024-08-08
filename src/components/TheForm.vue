<template>
  <form @submit.prevent="submitForm" center>
    <div class="degree-input">
      <label for="degree">Degree <span>*</span>: </label>
      <input type="number" v-model.number="degree" />
    </div>
    <div class="selectedTemp-input">
      <label for="selectedTemp">Temperature: </label>
      <select
        id="selectedTemp"
        name="selectedTemp"
        v-model="selectedTemp"
        required
      >
        <option value="celcius">Celcius</option>
        <option value="fahrenheit">Fahrenheit</option>
      </select>
    </div>

    <button>{{ btnText }}</button>
  </form>

  <ShowResult :result="result" :message="message" />
</template>

<script>
import ShowResult from "./ShowResult.vue";

export default {
  components: { ShowResult },
  data() {
    return {
      degree: null,
      selectedTemp: "celcius",
      result: null,
      btnText: "Convert",
      message: "",
    };
  },
  methods: {
    submitForm(e) {
      // the field must be filled
      if (this.degree === null && this.btnText === "Convert") {
        this.message = "*Please fill in the field";
        // convert when the field is filled
      } else if (this.result === null || this.degree !== null) {
        this.convertion();
        this.clearInputs();
        // reset form
      } else if (this.result !== null) {
        this.clearForm();
      }
    },
    convertion() {
      // convert Celcius to Fahrenheit
      const toFahrenheit = (this.degree * 9) / 5 + 32;

      // convert Fahrenheit to Celcius
      const toCelcius = ((this.degree - 32) * 5) / 9;

      // convert the selected temperature
      if (this.selectedTemp === "celcius") {
        this.message = "Converting...";
        setTimeout(() => {
          this.result = `${Math.round(parseFloat(toFahrenheit))} Fahrenheit`;
          this.message = "Click reset";
        }, 2500);
      } else if (this.selectedTemp === "fahrenheit") {
        this.message = "Converting...";
        setTimeout(() => {
          this.result = `${Math.round(parseFloat(toCelcius))} Celcius`;
          this.message = "Click reset";
        }, 2500);
      }
    },
    // clear data
    clearInputs() {
      this.degree = null;
      this.selectedTemp = "celcius";
      this.btnText = "Reset";
    },
    // reset form
    clearForm() {
      this.result = null;
      this.message = "";
      this.btnText = "Convert";
    },
  },
};
</script>
