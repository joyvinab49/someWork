<template>
  <div class="types">
    <select id="selectIt" v-model="selected" :typeName="selected">
      <option disabled value="">any type</option>
      <option ref="todotypes" v-for="(type, index) in alltypes" :key="index">
        {{ type.typeName }}
      </option>
    </select>
  </div>
</template>

<script>
import mediator from "../model/mediator";
export default {
  name: "types",
  data() {
    return {
      selected: "",
    };
  },
  props: {
    alltypes: {
      type: Array,
    },
  },
  created: function () {
    mediator.$on("select", (val) => {
      this.selected = val;
    });
    mediator.$on("return", () => {
      this.selected = "";
    });
  },
};
</script>

<style scoped>
.types {
  display: inline-block;
}

#selectIt {
  color: rgb(34, 148, 148);
  font-weight: bold;
  width: 95px;
  height: 40px;
  outline: none;
  vertical-align: bottom;
  margin-right: 10px;
  font-size: 16px;
}
</style>