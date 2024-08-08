<template>
  <div class="container">
    <TheHeader />
    <TheForm />
    <TheFooter />
  </div>
</template>

<script>
import TheHeader from "./components/TheHeader.vue";
import TheForm from "./components/TheForm.vue";
import TheFooter from "./components/TheFooter.vue";

export default {
  name: "App",
  components: { TheHeader, TheForm, TheFooter },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: end;
  margin-top: 90px;
}
.container {
  width: 46%;
  min-width: 320px;
  display: flex;
  flex-direction: column;
  align-items: center;
  margin-left: auto;
  margin-right: 36px;
  background-color: rgba(255, 255, 255, 0.6);
  border-radius: 12px;
  height: 70vh;
}
@media (max-width: 425px) {
  .container {
    margin: 0 auto;
  }
}
</style>
