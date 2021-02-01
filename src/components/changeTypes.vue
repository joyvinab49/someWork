<template>
  <select v-model="seleType" @change="msgNew" ref="typeNames">
    <option v-for="(type, index) in msg" :key="index">
      {{ type.typeName }}
    </option>
  </select>
</template>

<script>
export default {
  name: "changeTypes",
  data() {
    return {
      seleType: "",
    };
  },
  props: {
    msg: {
      type: Array,
    },
  },
  methods: {
    msgNew() {
      this.$emit("input", this.seleType);
    },
  },
};
</script>

<style scoped>
</style>