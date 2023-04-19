<template>
    <div class="">
        <h1 class="text-center">List of Users</h1>
        <div class="text-center card shadow-sm mx-auto my-3 pt-3" v-for="user in allUsers" v-bind:key="user.id">
            <p>{{ user.name }}</p>
            <p>{{ user.username }}</p>
            <p>{{ user.email }}</p>
        </div>
    </div>
</template>

<script>
    import axios from "axios";
    export default {
        data () {
            return {
                allUsers: [],
            }
        },
        mounted(){
            this.getUsers();
        },
        methods: {
            getUsers (){
                let url = 'https://jsonplaceholder.typicode.com/users';
                axios.get(url).then((response)=>{
                    this.allUsers = response.data
                    console.log(this.allUsers);
                })
            }
        }
    }
</script>

<style>
    @media (min-width: 1024px) {
        .about {
        min-height: 100vh;
        display: flex;
        align-items: center;
        }
    }
</style>
