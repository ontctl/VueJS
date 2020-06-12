<template>
  <div>
    <h3 class="display-1">Günlük</h3>
    <table class="table">
      <thead class="thead-dark">
        <tr>
          <th>Başlık</th>
          <th>Tarih</th>
          <th>Resim</th>
          <th>Günlük Numarası</th>
          <th></th>
        </tr>
      </thead>

      <tbody>
        <tr v-for="product in products" :key="product.id">
          <td>{{product.ItemName}}</td>
          <td>{{product.ItemPrice}} tl</td>
          <td>
            <img :src="product.PictureUrl" width="128" height="128" class="img-thumbnail" />
          </td>
          <td>{{product.StockCount}}</td>
          <td>
            <button type="button" class="btn btn-success">Satın Al</button>
          </td>
        </tr>
      </tbody>
    </table>

    <div class="alert alert-success" role="alert">Sepet!</div>
  </div>
</template>


<script>
export default {
  name: "product-list",
  props: {
    products: Array
  }
};
</script>


<style scoped>
td {
  margin: 40px 0 0;
}
</style>