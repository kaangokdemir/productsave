<template>
    <div class="container">
        <app-header></app-header>
        <app-new-product></app-new-product>
        <app-progress></app-progress>
        <app-products></app-products>
        <app-footer></app-footer>
    </div>

</template>

<script>
import Header from "./components/Header";
import NewProduct from "./components/NewProduct";
import Progress from "./components/Progress";
import Products from "./components/Products";
import Footer from "./components/Footer";

export default {
    components: {
        appHeader: Header,
        appNewProduct: NewProduct,
        appProgress: Progress,
        appProducts: Products,
        appFooter: Footer
    }
};
</script>

<style>
html {
  position: relative;
  min-height: 100%;
}
body {
    height: 100;
    background-color: #e0dbeb;
    padding-top: 20px;
    padding-bottom: 20px;
    margin-bottom: 80px;
}
.card {
    margin-right: 5px;
    margin-bottom: 5px;
}

.card:last-child {
    margin-right: 5px;
}
.col-sm-6 {
    max-width: 50% !important;
}

.firstpic {
    max-width: 290px;
}

@media only screen and (min-width: 600px) {
    .saran {
        max-width: 15.666667% !important;
    }
}
@media only screen and (max-width: 600px) {
    .product-container {
        margin-left: -10px;
    }
    #firstcard{
      margin-left: 5px;
    }
}
</style>

