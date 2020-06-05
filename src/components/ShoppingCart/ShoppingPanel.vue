<template>
    <div class="container">
        <h2>TODO: ShoppingPanel</h2>
    </div>
</template>

<script>
    export default {
        name: "ShoppingPanel",
        data: function () {
            return {
                products: [
                    {
                        name: "Peras",
                        price: 2.54,
                        photo: './Single_apple.png',
                        stock: 20
                    },
                    {
                        name: "Manzanas",
                        price: 2.54,
                        photo: './Single_apple.png',
                        stock: 20
                    },
                    {
                        name: "Papayas",
                        price: 2.54,
                        photo: './Single_apple.png',
                        stock: 20
                    },
                    {
                        name: "Aguacates",
                        price: 2.54,
                        photo: './Single_apple.png',
                        stock: 20
                    },
                    {
                        name: "Bananas",
                        price: 2.54,
                        photo: './Single_apple.png',
                        stock: 20
                    },
                    {
                        name: "Verdes",
                        price: 2.54,
                        photo: './Single_apple.png',
                        stock: 20
                    },
                    {
                        name: "Maduros",
                        price: 2.54,
                        photo: './Single_apple.png',
                        stock: 20
                    },
                    {
                        name: "Piñas",
                        price: 2.54,
                        photo: './Single_apple.png',
                        stock: 20
                    },
                ],
                userCart: [

                ],
            }
        },
        methods: {
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