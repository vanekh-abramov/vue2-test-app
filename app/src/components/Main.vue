<template>
  <div class="container">
    <div class="theme_container">
      <p>THEME</p>
      <p>LIGHT</p>
      <p>BLACK</p>
    </div>
    <div class="selects_container">
      <MySelect :options="options" :isMultiple="true" v-model="selected" />
    </div>
  </div>
</template>

<script>
import MySelect from "./castomSelect/MySelect.vue";

export default {
  name: "MainComponent",
  components: {
    MySelect,
  },
  data() {
    return {
      options: [
        { name: "option 1", value: 1 },
        { name: "option 2", value: 2 },
        { name: "option 3", value: 3 },
        { name: "option 4", value: 4 },
        { name: "option 5", value: 5 },
        { name: "option 6", value: 6 },
        { name: "option 7", value: 7 },
        { name: "option 8", value: 8 },
        { name: "option 9", value: 9 },
        { name: "option 10", value: 10 },
        { name: "option 11", value: 11 },
        { name: "option 12", value: 12 },
        { name: "option 13", value: 13 },
        { name: "option 14", value: 14 },
        { name: "option 15", value: 15 },
        { name: "option 16", value: 16 },
        { name: "option 17", value: 17 },
        { name: "option 18", value: 18 },
        { name: "option 19", value: 19 },
        { name: "option 20", value: 20 },
      ],
      selected: [],
    };
  },
};
</script>

<style scoped lang="scss">
.container {
  display: flex;
  flex-direction: column;
}

div.theme_container {
  display: flex;
  p {
    font-family: "Roboto";
    font-style: normal;
    margin-right: 15px;
    font-weight: 400;
    font-size: 13px;
    line-height: 15px;
    color: #000000;
    &:first-child {
      margin-right: 29px;
    }
  }
}
</style>
