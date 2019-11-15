<template>
  <div class="container">
    Showing elements of async iterator:
    <ul>
      <li v-for="value in values" :key="value">
        {{ value }}
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  data() {
    return {
      values: []
    };
  },
  async created() {
    for await (const value of this.asyncIterable()) {
      this.values.push(value);
    }
  },
  methods: {
    async *asyncIterable() {
      for (let i = 0; i < 10; i++) {
        yield Promise.resolve(i);
      }
    }
  }
};
</script>
