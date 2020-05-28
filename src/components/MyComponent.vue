<template>
    <div>
        <!-- Interpolación de texto -->
        <h2>{{myText}}</h2>
        <!-- v-model 2 way data binding -->
        <div>
            <label for="texto">Texto a mostrar: </label>
            <input id="texto" v-model="myText"/>
        </div>
        <div>
            <button v-on:click="shouldShow = !shouldShow">
                Cambiar visibilidad</button>
            <!-- Ejemplos de v-if y v-else -->
            <h2 v-if="shouldShow">
            Ahora me ves
            </h2>
            <h2 v-else>
                Ahora no me ves
            </h2>
        </div>
        <div class="btn-holder">
            <button v-on:click="addItem">
            Añadir un número a la lista
        </button>
        <button v-on:click="removeItem">
            Remover un número a la lista
        </button>
        </div>
        <div class="shorter">
            <ul>
                <li v-for="item in listItems" :key="item">
                    {{item}}
                </li>
            </ul>
        </div>
    </div>
</template>

<script>
export default {
    data: function () 
    {
        return {
            myText: "Edita el cuadro de abajo para cambiar el texto!",
            shouldShow: false,
            listItems: [
                1,2,3,4
            ]
        }
    },
    methods: {
        addItem: function() {
            this.listItems.push(this.listItems.length + 1)
        },
        removeItem: function(){
            this.listItems.pop()
        }
    }

}
</script>
<style scoped>
template{
    box-sizing: border-box;
}
h2{
    color: green;
}

div {
    padding: 5px;
}

.btn-holder {
    display: flex;
    justify-content: space-evenly;

}

.shorter {
    width: 20%;
}


</style>

