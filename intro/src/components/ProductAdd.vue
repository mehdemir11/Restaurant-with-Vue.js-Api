<template>
  <div id="addForm">
    <form @submit.prevent="handleAdd">
      <div class="form-group">
        <label for="id"> ID </label>
        <input v-model="product.id" type="text" class="form-control" id="id" />
      </div>
      <div class="form-group">
        <label for="categoryId"> Category </label>
        <input v-model="product.categoryId" type="text" class="form-control" id="categoryId" />
      </div>
      <div class="form-group">
        <label for="productName"> Product Name </label>
        <input v-model="product.productName" type="text" class="form-control" id="productName" />
      </div>
      <div class="form-group">
        <label for="quantityPerUnit"> Description </label>
        <input v-model="product.quantityPerUnit" type="text" class="form-control" id="quantityPerUnit" />
      </div>
      <div class="form-group">
        <label for="unitPrice"> Unit Price </label>
        <input v-model="product.unitPrice" type="text" class="form-control" id="unitPrice" />
      </div>
      <div class="form-group">
        <label for="unitsInStock"> Units in Stock </label>
        <input v-model="product.unitsInStock" type="text" class="form-control" id="unitsInStock" />
      </div>
      <button type="submit" class="btn btn-md btn-outline-primary">Add</button>
    </form>
  </div>
</template>
<script>
export default {
  name: "product-add",
  data() {
    return {
      product: {
        id: "",
        categoryId: "",
        productName: "",
        quantityPerUnit: "",
        unitPrice: "",
        unitsInStock: "",
      },
    };
  },
  methods:{
    handleAdd(){
        this.$emit("add:product",this.product)
    }
  }
};
</script>
<style scoped>
#addForm{
    margin-left:100px
}
#addForm{
    margin-right:100px
}
</style>
