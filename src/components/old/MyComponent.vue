<template>
    <div>
        <h1>Interpolación de texto</h1>
        <!-- Interpolación de texto -->
        <h2>{{myText}}</h2>
        <!-- v-model 2 way data binding -->
        <div>
            <label for="texto">Texto a mostrar: </label>
            <input id="texto" v-model="myText"/>
        </div>
        <h1>v-if reactivo</h1>
        <div>
            <button v-on:click="shouldShow = !shouldShow">
                Cambiar visibilidad</button>
            <!-- Ejemplos de v-if y v-else -->
            <h2 v-if="shouldShow">
            Ahora me ves
            </h2>
            <h2 v-else-if="myText.length == 0">
                El texto de abajo esta vacio
            </h2>
            <h2 v-else>
                Ahora no me ves
            </h2>
            <!-- Ejemplo de v-show -->
            <h2 v-show='shouldShow'>Ahora me ves</h2>
        </div>
        <h1>Vista de lista con v-for, con reactividad</h1>
        <div class="btn-holder">
            <button v-on:click="addItem">
            Añadir un número a la lista
        </button>
        <button v-on:click="removeItem">
            Remover un número a la lista
        </button>
        </div>
        <div>
            <ul class="list">
                <li v-for="item in listItems" :key="item">
                    Elemento {{item}}
                </li>
            </ul>
        </div>
        <h2>
            Fotos pasadas al componente!
        </h2>
        <button v-on:click="fetchProfiles">Descargar fotos</button>
        <h2 v-if="felicitarUser != null">
            Felicitaciones a {{felicitarUser}}
        </h2>
        <div class="user-profiles">
            <user-component 
            v-for="user in fetchedUsers" 
            v-on:felicitar="onFelicitar" 
            v-bind:imgUrl="user.picture.large"
            v-bind:userModel="user" 
            :key="user.email"></user-component>
        </div>
        <form >
            <label for="nombre"></label>
            <input type="text" id="nombre">
            <button v-on:click.prevent="window.alert('Subido')">Subir datos</button>
        </form>
    </div>
</template>

<script>
import UserComponent from './UserComponent.vue'
export default {
    name: 'MyComponent',
    mounted: function() {
        console.log("Elemento montado");
    },
    components: {
        UserComponent
    },
    data: function () 
    {
        return {
            myText: "Edita el cuadro de abajo para cambiar el texto!",
            shouldShow: false,
            listItems: [
                1,3,4,2
            ],
            fetchedUsers: [],
            felicitarUser: null
        }
    },
    methods: {
        addItem: function() {
            this.listItems.push(this.listItems.length + 1)
        },
        removeItem: function(){
            this.listItems.pop()
        },
        fetchProfiles: async function () {
            let data = await fetch("https://randomuser.me/api?results=5").then((response) => response.json())
            this.fetchedUsers = data['results'];
        },
        onFelicitar: function(event){
            this.felicitarUser = event
        }
    },

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
.list {
    width: 20%;
    list-style-type: none;
    margin: 0;
    padding: 5px;
}
.user-profiles{
    display: flex;
    justify-content: space-around;
}
</style>

