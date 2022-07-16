<template>
    <div class="product-card">
        <img :src="imgUrl" width="300">
        <div class="product-card__info">
            <h2>{{title}}</h2>
            <p class="price">{{price}} ₽</p>
            <p class="count">Доступно для доставки: {{count}}</p>
            <button @click="addToBasket" type="button">Добавить в корзину</button>
        </div>
    </div>
</template>

<script>
export default {
    name: 'ProductCard',
    props: {
        title: {
            type: String,
            // Валидатор данных (валидирует наш prop). Возвращает bool
            validator(value) {
                return value.length < 50;
            },
        },
        price: {
            type: Number,
            // Обязательное значение. По умолчанию - false
            required: true,
        },
        imgUrl: {
            type: String,
            // Значение по умолчанию
            default: ""
        },
        count: {
            type: Number,
            default: 0
        },
    },
    methods: {
        addToBasket() {
            this.$emit('addToBasket')
        }
    }
}
</script>


<style lang="scss" scoped>
.product-card {
    width: 300px;
    border: 1px solid rgb(211, 211, 211);
    padding: 20px 15px;

    &__info {
        margin-top: 20px;

        h2,
        .price {
            font-weight: 500;
        }

        .count {
            color: rgb(143, 143, 143);
        }

        button {
            background-color: rgb(221, 56, 56);
            color: #fff;
            border: none;
            border-radius: 4px;
            padding: 8px 14px;
            display: block;
            cursor: pointer;
            margin-top: 20px;
        }
    }
}
</style>