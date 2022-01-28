<template>
  <v-text-field
    @input="handleInput"
    v-model="userName"
    :label="label"
  ></v-text-field>
</template>

<script>
export default {
  name: "text-input",
  props: ["label"],
  data() {
    return {
      userName: null,
    };
  },
  methods: {
    handleInput() {
      this.$emit("textinput", this.userName);
    },
  },
};
// kuda mne emit pisat? pojalusta na pomosh'
</script>

<style></style>
