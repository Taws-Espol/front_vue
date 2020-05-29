<template>
    <div>
        <div class="user">
            <img v-bind:src="imgUrl" />
            <h2>Nombre: {{name}}</h2>
            <h2>Telefono: {{phone}}</h2>
        </div>
    </div>
</template>

<script>
export default {
    name: 'user-component',
    props: [
        'imgUrl', 
        'userModel'
    ],
    data: function(){
        return {
            name: this.userModel.name.first,
            phone: this.userModel.phone
        }
    }
}
</script>

<style scoped>
.user {
    margin: grey 1px;
}
</style>