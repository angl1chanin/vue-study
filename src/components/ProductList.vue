<template>
    <div class="product-list">
        <div class="flex top-information">
            <h1>Письменные столы</h1>
            <!-- Директива v-model выполняет действия v-on и v-bind -->
            <SearchInput v-model="searchText" />
            <!-- <input type="text" class="search" :value="searchText" @input="searchText = $event.target.value"> -->
            <button @click="loadSearch">Найти</button>
            <ul class="list-default flex">
                <li v-for="(product, index) in products" :key="index">
                    <ProductCard 
                    :title="product.title"
                    :price="product.price"
                    :img-url="product.imgUrl"
                    :count="product.count"
                    @addToBasket="addToBasket(index)"
                    />
                </li>
            </ul>
        </div>
    </div>
</template>

<script>
import ProductCard from './ProductCard'
import SearchInput from './SearchInput'

export default {
    name: 'ProductList',
    components: { ProductCard, SearchInput },
    data() {
        return {
            searchText: '',
            products: [
                {
                    title: 'Стол Jim',
                    price: 19999,
                    imgUrl: 'https://hoff.ru/upload/iblock/40f/40f9078f28557299c1ecedf5863a25b5.jpg',
                    count: 30
                },
                {
                    title: 'Стол Monako',
                    price: 17199,
                    imgUrl: 'https://hoff.ru/upload/iblock/af2/af2d37161f217d4f489373be7da4a7a0.jpg',
                    count: 20
                },
                {
                    title: 'Стол с двумя ящиками Кварт MD 768',
                    price: 10999,
                    imgUrl: 'https://hoff.ru/upload/iblock/1cc/1ccb33b50e3e9cfa08629bf455e41855.jpg',
                    count: 23
                }
            ]
        }
    },
    methods: {
        addToBasket(index) {
            console.log(index);
        },
        loadSearch() {
            console.log("Загрузить товары: ", this.searchText)
        }
    },
}
</script>

<style lang="scss" scoped>
.flex {
    display: flex;
}
li {
  margin-right: 20px;
  list-style-type: none;
}
.top-information {
    flex-direction: column;
  align-items: center;
  h1 {
    margin-bottom: 0;
  }
  button {
    background-color: rgb(221, 56, 56);
    color: #fff;
    border: none;
    border-radius: 4px;
    padding: 8px 14px;
    display: block;
    cursor: pointer;
    margin-left: 10px;
  }
  margin-bottom: 22px;
}
</style>