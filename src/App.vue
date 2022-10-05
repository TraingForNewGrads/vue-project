<script>
export default {
  data() {
    return {
      products: [
        {name: "重疾险产品"},
        {name: "财产险产品"},
        {name: "健康险产品"}
      ]
    }
  },
  computed: {
    // ...
  },
  methods: {
  }
}
</script>

<template>
  <select>
    <option v-for="product in products"> {{product.name}} </option>
  </select>
</template>

<style>
</style>