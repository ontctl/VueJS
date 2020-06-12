<template>
    <div id="app">
        <div id="nav">
            <img alt="Vue logo" src="./assets/logo.png" />
            <router-link v-if="authenticated" to="/login" v-on:click.native="logout()" replace>Logout</router-link>
            <login/>
            <secure/>
            <ProductList :products="products"/>
        </div>
        <router-view @authenticated="setAuthenticated" />
    </div>
</template>


<script>
import login from "./components/login.vue";
import secure from "./components/secure.vue";
import ProductList from "./components/ProductList.vue";

export default {
  name: "App",
  components: {
    login,
    secure,
    ProductList
  },
  data() {
    return {
      authenticated: false,
      mockAccount: {
        username: "admin",
        password: "123456"
      },
      products: [
        {
          ItemName: "HP Notebok XLS",
          ItemPrice: 2045.0,
          PictureUrl: "http://www.kibele.com/isu/HP.png",
          StockCount: 8
        },
        {
          ItemName: "Lenovo Notebok E490",
          ItemPrice: 3799.99,
          PictureUrl: "http://www.kibele.com/isu/LonovoE490.PNG",
          StockCount: 27
        },
        {
          ItemName: "Lenovo Notebok T440",
          ItemPrice: 4599.99,
          PictureUrl: "http://www.kibele.com/isu/LonovoT480.PNG",
          StockCount: 6
        },
        {
          ItemName: "Assus Notebok N5",
          ItemPrice: 3456.99,
          PictureUrl: "http://www.kibele.com/isu/AsusN5.PNG",
          StockCount: 80
        },
        {
          ItemName: "HP Pavillon 13",
          ItemPrice: 2799.99,
          PictureUrl: "http://www.kibele.com/isu/HPNotebokXLS.PNG",
          StockCount: 7
        },
        {
          ItemName: "Lenovo Notebok T480",
          ItemPrice: 2999.99,
          PictureUrl: "http://www.kibele.com/isu/LonovoT480.PNG",
          StockCount: 1
        }
      ]
    };
  },
  mounted() {
    if (!this.authenticated) {
      this.$router.replace({ name: "login" });
    }
  },
  methods: {
    setAuthenticated(status) {
      this.authenticated = status;
    },
    logout() {
      this.authenticated = false;
    }
  }
};
</script>



<style>
body {
  background-color: #f0f0f0;
}
h1 {
  padding: 0;
  margin-top: 0;
}
#app {
  width: 1024px;
  margin: auto;
}
</style>