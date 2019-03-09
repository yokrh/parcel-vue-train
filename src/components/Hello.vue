<template>
  <div>
    <h1 class="hello">{{hello}}</h1>
  </div>
</template>

<script lang="ts">
export default {
  props: {},
  data() {
    return {
      bundler: "Parcel",
    };
  },
  computed: {
    hello() {
      if (!this.bundler) return '';
      return `Hello ${this.bundler} !!`
    },
  },
  mounted() {
    console.log('[Hello.vue] mounted');
  },
  methods: {},
};
</script>

<style lang="postcss" scoped>
.hello {
  color: green;
}
</style>
