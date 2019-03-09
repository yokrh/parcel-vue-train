<template>
  <div>
    <p class="description">my-first-parcel-app</p>
    <p style="color:orange;">It's easy</p>

    <c-form :title="formTitle"></c-form>
  </div>
</template>

<script>
import FORM from '../constants/FORM';
import Form from './common/Form';

export default {
  components: {
    'c-form': Form,
  },
  props: {},
  data() {
    return {
      formTitle: FORM.TITLE,
    };
  },
  computed: {},
  mounted() {
    console.log('[Content.vue] mounted');
  },
  methods: {},
};
</script>

<style lang="postcss" scoped>
.description {
  color: blue;
}
</style>
