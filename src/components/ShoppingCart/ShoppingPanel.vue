<template>
    <div class="container-fluid">
        <div class="container" >
            <h2>Items en stock</h2>
            <div class="form-inline">
                <label class="col-form-label" for="searchId">Buscar: </label>
                <input type="text" id="searchId" v-model="searchTerm">
                <button class="float-right btn btn-dark" v-on:click="toggleSortingOrder">Ordenar por precio</button>
            </div>
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
                searchTerm: "",
                products: [],
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
            },
            fetchProducts: async function(){
                let reply = await fetch("./data.json").then(function(response) {
                    return response.json()
                });
                this.products = reply;

            }
        },
        computed: {
            getSearchTerm: function(term) {
                return this.products.filter((product) => product.name.includes(term));
            },
        },
        mounted: function() {
            this.fetchProducts();
        }
    }
</script>

<style scoped>

</style>