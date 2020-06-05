<template>
    <div class="container">
        <div class="row" id="searchBox">
            <label for="searchField">Buscar personas</label>
            <input id="searchField" type="text" v-model="searchTerm"/>
        </div>
        <div class="row">
            <user-component 
            v-for="user in filteredUsers" 
            v-bind:imgUrl="user.picture.large"
            v-bind:userModel="user" 
            :key="user.email"
            class="col-3"
            >
            </user-component>
        </div>
    </div>
</template>

<script>
import UserComponent from './UserComponent.vue';

export default {
    name: 'SearchComponent',
    components: {
        UserComponent
    },
    mounted: function(){
        this.fetchUsers();
    },
    data: function() {
        return  {
            searchTerm: '',
            users: []
        }
    },
    computed:{
        filteredUsers: function (){
            if(this.searchTerm){
                return this.users.filter(user => user.name.first.includes(this.searchTerm) || user.name.first.includes(this.searchTerm));
            }else {
                return this.users;
            }
        }
    },
    methods:{
        fetchUsers:  async function () {
            let data = await fetch("https://randomuser.me/api?results=50").then((response) => response.json())
            this.users = data['results'];
        }
    } 
}
</script>

<style>
#searchBox{
    display: flex;
    justify-content: center;
    padding: 10px;
}

#searchBox * {
    padding: 10px;
}
</style>