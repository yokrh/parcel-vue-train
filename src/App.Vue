<template>
  <div>
    <c-hello></c-hello>
    <c-content></c-content>
  </div>
</template>

<script>
import Vue from "vue";
import Hello from "./components/Hello";
import Content from "./components/Content";

export default Vue.extend({
  components: {
    'c-hello': Hello,
    'c-content': Content,
  },
  props: {},
  data() {
    return {};
  },
  computed: {},
  mounted() {
    const msg = this.getMsg();
    console.log(msg);
  },
  methods: {
    getMsg() {
      return "[App.Vue] mounted";
    },
  },
});
</script>

<style>
</style>
