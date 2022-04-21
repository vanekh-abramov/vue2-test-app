<template>
  <div class="my_select">
    <p @click="areOptionsVisible = !areOptionsVisible" class="title">Select</p>
    <div v-if="areOptionsVisible" class="options">
      <input
        class="input"
        type="text"
        name="search"
        placeholder="Search"
        v-on:input="searching(searchingElement, options)"
        v-model="searchingElement.text"
      />
      <p
        :class="{ active: isSelectedOption(option) }"
        @click="selectOption(option)"
        v-for="option in options"
        :key="option.value"
      >
        {{ option.name }}
      </p>
    </div>
  </div>
</template>

<script>
export default {
  name: "MySelect",
  model: {
    prop: "value",
    event: "input",
    options: [],
  },
  props: {
    options: {
      type: Array,
      default() {
        return [];
      },
    },
    isMultiple: Boolean,
    value: {},
  },
  methods: {
    searching(searchingElement, option) {
      if (option) {
        option.filter((item) =>
          item.name
            .toLowerCase()
            .includes(this.searchingElement.text.toLowerCase())
        );
        console.log(option);
      }
      return option;
    },
    isSelectedOption(option) {
      if (this.isMultiple) {
        return this.value.find((item) => item === option) !== undefined;
      } else {
        return this.value === option;
      }
    },
    selectOption(option) {
      if (this.isMultiple) {
        let exists = this.value.find((item) => item === option);
        if (exists) {
          this.$emit(
            "input",
            this.value.filter((item) => item !== option)
          );
        } else {
          this.$emit("input", [...this.value, option]);
        }
      } else {
        this.$emit("input", option);
      }
    },
  },
  data() {
    return {
      areOptionsVisible: false,
      searchingElement: {
        text: "",
      },
    };
  },
};
</script>

<style scoped lang="scss">
.my_select {
  position: relative;
  width: 200px;
  text-align: center;
  .title {
    border: 1px solid black;
    cursor: pointer;
    height: 35px;
    transition: all 0.1s linear;
    &:hover {
      border: 2px solid black;
    }
  }
  .options {
    position: absolute;
    top: 45px;
    right: 0;
    border: 1px solid black;
    width: 100%;
    height: 200px;
    overflow-y: auto;
    border: 1px solid #c4c4c4;
    border-radius: 5px;
    &::-webkit-scrollbar {
      width: 5px;
      background-color: #4f4f4f;
      opacity: 0.2;
      border-radius: 5px;
    }
    &::-webkit-scrollbar-thumb {
      background-color: #828282;
      opacity: 0.6;
      border-radius: 5px;
    }
    .input {
      width: 90%;
      height: 30px;
      padding: 9px;
      border-radius: 5px;
      margin: 10px 0;
    }
    .active {
      background-color: rgb(173, 25, 25);
    }
    p {
      height: 40px;
      margin: 0;
      cursor: pointer;
      transition: all 0.3s linear;
      &:hover {
        background-color: rgb(92, 89, 89);
      }
    }
  }
}
</style>
