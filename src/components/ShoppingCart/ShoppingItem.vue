<template>
    <div>
        <div class="card">
            <img class="card-img-top" v-bind:src="item.photo">
            <div class="card-body">
                <h5 class="card-title">{{item.name}}</h5>
                <p class="card-text">Stock: {{item.stock}}</p>
                <p class="card-text">Precio: ${{item.price.toFixed(2)}}</p>
                <div class="btn-group">
                    <button class="btn btn-primary">Add to Cart</button>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
    export default {
        name: "ShoppingItem",
        props: {
            item: Object
        },
        methods: {
            addToCart: function(){
                this.$emit('addToCart', this.item);
            }
        }

    }
</script>

<style scoped>
    img {
        width: 200px;
        height: 200px;
    }
</style>