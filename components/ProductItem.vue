<template>
    <div class="bg-purple">
        <el-container class="product-container">
            <el-main class="product-item">
                        <div class="grid-content bg-purple product-item__column">
                            <div class="product-item__image-block">  
                                <img
                                    class="product-item__image"
                                    src="../assets/images/phone.jpg"
                                    :alt="productImageDescription"
                                />
                                <div class="product-item__quick-look">Быстрый просмотр</div>
                                <div class="product-item__sale">{{sale}}</div>
                            </div>
                            <div class="product-item__description">
                                <div class="product-item__price">
                                    {{formatToRub(price)}} ₽
                                    <span class="product-item__old-price">{{formatToRub(oldPrice)}}  ₽</span>
                                </div>
                                <div class="product-item__cardPrice">{{formatToRub(cardPrice)}}  ₽</div>
                                <div class="product-item__specification">
                                    Apple / Смартфон Iphone 12pro 128GB / 6.1" / 2531x1170 / OLED / 128 ГБ
                                </div>
                                <div class="product-item__stars-images">
                                    <img class="product-item__star"
                                        src="../assets/images/star.png"
                                        v-for="star in this.stars"
                                    />
                                    <div class="product-item__stars-count">87</div>
                                </div>
                            </div>
                            <div class="buy">
                                <button class="buy__installment">рассрочка 0-0-6</button>
                                <div class="basket">
                                    <button class="basket__btn">В корзину</button>
                                    <img 
                                    @click="like"
                                    src="../assets/images/heart.png"
                                    class="like"
                                    />
                                </div>
                            </div>

                        </div>
                </el-main>
        </el-container>
    </div>
</template>

<script>
      export default {
        data() {
            return {
                productName: 'Phone',
                productDescription: 'Phone',
                productImageDescription: 'Phone description',
                productImageStyle: {
                    'border-radius': '15px'
                },
                sale: '-14%',
                oldPrice: 99990,
                price: 86956,
                cardPrice: 85251,
                // я так думаю звездочки надо будет как раскрашивать исходя из какого-то значения, может быть от 1 до 5, где 5 полностью закрашена...
                stars: [5,5,5,5,5],
            }
        },
        methods: {
            formatToRub(price) {
                //return new Intl.NumberFormat("ru").format(price);
                return  new Intl.NumberFormat("ru", {style: "decimal", symbol: 'Р'}).format(price);

            },
            like() {
                console.log("like");
            }
        }
    }
</script>

<style>
    /* Это не настоящий макет в фигме, поэтому все размеры беру примерные */
    *{
        --purple-color: #cb2bab;
        --pink-color: #fdeef9;
        --gray-color: #8b8b8b;
        --light-gray-color: #999999;
    }
    .product-container{
        padding: 20px;
        width: 400px;
    }
    .el-col {
        border-radius: 4px;
    }
    .bg-purple-dark {
        background: #99a9bf;
    }
    .bg-purple {
        background: #d3dce6;
    }
    .bg-purple-light {
        background: #e5e9f2;
    }
    .grid-content {
        border-radius: 4px;
        min-height: 36px;
        padding: 2px;
    }
    .product-item__column{
        background-color: white;
        border-radius: 18px;
    }
    .product-item__image {
        width: 100%;
        border-radius: 20px;
    }
    .product-item__image-block {
        position: relative;
        text-align: center;
    }
    .product-item__quick-look {
        position: absolute;
        top: 50%;
        left: 50%;
        transform: translate(-50%, -50%);
        padding: 10px;
        background-color: white;
        opacity: 0.85;
        border-radius: 20px;
        cursor: pointer;
    }
    .product-item__sale {
        position: absolute;
        bottom: 10%;
        left: 10%;
        color: var(--purple-color);
        border-radius: 20px;
        background-color: white;
        padding: 2px 5px;
        font-size: smaller;
        background-color: var(--pink-color);
        opacity: 0.9;
    }
    .product-item__description {
        padding: 0 20px 0 20px;
    }
    .product-item__price {
        font-size: 20px;
        font-weight: bold;
        display: flex;
        align-items: center;
        gap: 10px;
    }
    .product-item__old-price {
        font-size: 14px;
        text-decoration: line-through;
        color: var(--gray-color);
    }
    .product-item__cardPrice {
        color: var(--purple-color);
        padding: 5px 0;
        font-weight: bold;
    }
    .product-item__specification {
        color: var(--light-gray-color);
    }
    .product-item__stars-images {
        display: flex;
        gap: 5px;
        color: var(--light-gray-color);
        font-size: 14px;
        padding: 7px 0 5px 0;
    }
    .buy {
        padding: 8px 20px;
    }
    .buy__installment {
        padding: 7px 12px;
        background: rgb(210,254,237);
        background: linear-gradient(90deg, rgba(210,254,237,1) 0%, rgba(236,251,75,1) 100%);
        border-radius: 26px;
        border: none;
        cursor: pointer;
        font-size: medium;
        text-transform: uppercase;
    }
    .basket {
        display: flex;
        gap: 20px;
        padding: 20px 0;
    }
    .basket__btn {
        cursor: pointer;
        font-size: medium;
        background-color: var(--purple-color);
        color: white;
        border-radius: 6px;
        border: none;
        font-size: small;
        padding: 7px 25px;
    }
    .like{
        cursor: pointer;
    }
</style>