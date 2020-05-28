<template>
    <div>
        <!-- Interpolación de texto -->
        <h2>{{myText}}</h2>
        <button v-on:click="shouldShow = !shouldShow">
            Cambiar visibilidad</button>
        <!-- Ejemplos de v-if y v-else -->
        <div v-if="shouldShow">
            Now you see me
        </div>
        <div v-else>
            Now you don't
        </div>
        <button v-on:click="listItems.push(listItems.length + 1)">
            Añadir un número a la lista
        </button>
        <button v-on:click="listItems.pop()">
            Remover un número a la lista
        </button>
        <ul>
           <li v-for="item in listItems" :key="item">
               <h2>{{item}}</h2>
           </li>
        </ul>
        
    </div>
</template>

<script>
export default {
    data: function () 
    {
        return {
            myText: "Texto de ejemplo",
            shouldShow: true,
            listItems: [
                1,2,3,4
            ]
        }
    }

}
</script>
<style scoped>
h2{
    color: green;
}

</style>

