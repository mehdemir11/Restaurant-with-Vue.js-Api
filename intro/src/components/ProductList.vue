<template>
  <div class="form-floating mb-3" id="list">
    <p v-if="products.length == 0">
      There is no product here!
      <a href="http://localhost:8080">Are you lost?</a>
    </p>
    <table v-else class="table">
      <thead>
        <tr>
          <th>ID</th>
          <th>Product Name</th>
          <th>Description</th>
          <th>Unit Price</th>
          <th>Units in Stock</th>
          <th>Action(s)</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="product in products" :key="product.id">
          <td v-if="updateId === product.id">
            <input
              v-model="product.id"
              type="text"
              class="form-control"
              id="productId"
            />
          </td>
          <td v-else>{{ product.id }}</td>
          <td v-if="updateId === product.id">
            <input
              v-model="product.productName"
              type="text"
              class="form-control"
              id="productName"
            />
          </td>
          <td v-else>{{ product.productName }}</td>
          <td v-if="updateId === product.id">
            <input
              v-model="product.quantityPerUnit"
              type="text"
              class="form-control"
              id="quantityPerUnit"
            />
          </td>
          <td v-else>{{ product.quantityPerUnit }}</td>
          <td v-if="updateId === product.id">
            <input
              v-model="product.unitPrice"
              type="text"
              class="form-control"
              id="unitPrice"
            />
          </td>
          <td v-else>{{ product.unitPrice }}</td>
          <td v-if="updateId === product.id">
            <input
              v-model="product.unitsInStock"
              type="text"
              class="form-control"
              id="unitsInStock"
            />
          </td>
          <td v-else>{{ product.unitsInStock }}</td>
          <td v-if="updateId !== product.id">
            <button
              class="btn btn-md btn-outline-primary"
              @click="handleUpdate(product)"
            >
              ✐
            </button>
            <button
              class="btn btn-md btn-outline-danger"
              @click="handleDelete(product)"
            >
              🗑️
            </button>
          </td>
          <td v-else>
            <button
              class="btn btn-md btn-outline-primary"
              @click="handleSave(product)"
            >
            ✓
            </button>
            <button
              class="btn btn-md btn-outline-danger"
              @click="updateId=null"
            >
              ×
            </button>
          </td>
        </tr>
      </tbody>
    </table>
  </div>
</template>
<script>
export default {
  name: "product-list",
  data() {
    return { updateId: null };
  },
  props: {
    products: Array,
  },
  methods: {
    handleDelete(product) {
      this.$emit("delete:product", product);
    },
    handleUpdate(product) {
      this.updateId = product.id;
    },
    handleSave(product){
      this.$emit("update:product",product)
      this.updateId=null
    }
  },
};
</script>
<style scoped>
a {
  text-decoration: none;
}
.table{
  margin-top: 20px;
}
#list{
    margin:100px
}
</style>
