<script>
export default {
  data() {
    return {
      products: [
        {id: 'dread-disease-insurance', name: '重疾险产品'},
        {id: 'property-insurance', name: '财产险产品'},
        {id: 'health-insurance', name: '健康险产品'}
      ],
      selectedProduct: '',
      inputParam: null
    }
  },
  methods: {
    submit() {
      let data;
      switch (this.selectedProduct) {
        case "dread-disease-insurance":
          data = {
            gender: this.inputParam
          }
          break
        case "property-insurance":
          data = {
            value: this.inputParam
          }
          break
        case "health-insurance":
          data = {
            age: this.inputParam
          }
          break
        default:
          alert("wrong type of product")
      }
      fetch('/api/' + this.selectedProduct, {
        method: 'POST',
        headers: {
          'Content-Type': 'application/json',
        },
        body: JSON.stringify(data),
      })
          .then((data) => {
            if(data.status !== 200) {
              data.text().then(error => alert("异常: " + error))
            } else {
              data.json().then(data => alert("保费：" + data.totalAmount))
            }
          })
    }
  }
}
</script>

<template>
  <h3>产品列表</h3>
  <select v-model="selectedProduct">
    <option v-for="product in products" :value="product.id"> {{ product.name }}</option>
  </select>
  <div v-if="selectedProduct === 'dread-disease-insurance'">请输入性别：<input v-model="inputParam"></div>
  <div v-if="selectedProduct === 'property-insurance'">请输入房价：<input v-model="inputParam"></div>
  <div v-if="selectedProduct === 'health-insurance'">请输入年龄：<input v-model="inputParam"></div>
  <button @click="submit">提交</button>
</template>

<style>
</style>