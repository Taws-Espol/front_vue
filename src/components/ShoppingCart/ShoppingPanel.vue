<template>
    <div class="container-fluid">
        <div class="container" >
            <h2>Items en stock</h2>
            <button class="btn btn-dark" v-on:click="toggleSortingOrder">Ordenar por precio</button>
            <div class="row">
                <shopping-item
                        style="padding-top: 10px;"
                        class="col-4"
                        v-bind:item="product"
                        v-for="product in products" :key="product.id"
                ></shopping-item>

            </div>
        </div>

    </div>
</template>

<script>
    import ShoppingItem from "./ShoppingItem";
    export default {
        name: "ShoppingPanel",
        components: {ShoppingItem},
        data: function () {
            return {
                descending: false,
                products: [
                    {
                        id: 1,
                        name: "Peras",
                        price: 2.57,
                        photo: './pear.png',
                        stock: 20
                    },
                    {
                        id: 2,
                        name: "Manzanas",
                        price: 1.83,
                        photo: './Single_apple.png',
                        stock: 20
                    },
                    {
                        id: 3,
                        name: "Papayas",
                        price: 2.54,
                        photo: './papaya.png',
                        stock: 20
                    },
                    {
                        id: 4,
                        name: "Aguacates",
                        price: 3.54,
                        photo: './aguacate.png',
                        stock: 20
                    },
                    {
                        id: 5,
                        name: "Bananas",
                        price: 1.25,
                        photo: './bananas.png',
                        stock: 20
                    },
                    {
                        id: 6,
                        name: "Verdes",
                        price: 1.85,
                        photo: './verde.png',
                        stock: 20
                    },
                    {
                        id: 7,
                        name: "Maduros",
                        price: 1.50,
                        photo: './bananas.png',
                        stock: 20
                    },
                    {
                        id: 8,
                        name: "Piñas",
                        price: 3.50,
                        photo: './pina.png',
                        stock: 20
                    },
                ],
                userCart: [

                ],
            }
        },
        methods: {
            toggleSortingOrder: function(){
                this.descending = !this.descending;
                this.sortProductsByPrice(this.descending);
            },
            sortProductsByPrice: function(descending = false){
                if (descending) {
                    this.products.sort((a,b) => b.price - a.price);
                } else {
                    this.products.sort((a, b) => a.price - b.price);
                }
            }
        },
        computed: {
            getSearchTerm: function(term) {
                return this.products.filter((product) => product.name.includes(term));
            },
        }
    }
</script>

<style scoped>

</style>