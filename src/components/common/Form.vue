<template>
  <div>
    <div>{{title}}</div>
    <input v-model="name">
    <button @click="onClickButton">Button</button>
  </div>
</template>

<script>
export default {
  props: {
    title: {
      default: 'default-form-title',
    },
  },
  data() {
    return {
      name: 'default-name',
    };
  },
  computed: {},
  mounted() {
    console.log('[Form.vue] mounted');
  },
  methods: {
    onClickButton() {
      window.alert(`Your name is ${this.name}.`);
    },
  },
};
</script>

<style>
</style>
