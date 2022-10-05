<script>
export default {
  data() {
    return {
      products: [
        {id: 'dread-disease-insurance', name: '重疾险产品'},
        {id: 'property-insurance', name: '财产险产品'},
        {id: 'health-insurance', name: '健康险产品'}
      ],
      selectedProduct: {id: '', name: ''}
    }
  }
}
</script>

<template>
  <select v-model="selectedProduct">
    <option v-for="product in products" :value="product"> {{product.name}} </option>
  </select>
  <h3 v-if="selectedProduct.id === 'dread-disease-insurance'">请输入性别</h3>
  <h3 v-if="selectedProduct.id === 'property-insurance'">请输入房价</h3>
  <h3 v-if="selectedProduct.id === 'health-insurance'">请输入年龄</h3>
</template>

<style>
</style>