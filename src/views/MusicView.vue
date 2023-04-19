<script setup>
    import { RouterLink } from 'vue-router';
</script>
<template>
    <input type="checkbox" name="" id="check">
    <label for="check">
        <i class="fas fa-bars" aria-hidden="true" id="btn"></i>
        <i class="fas fa-times" aria-hidden="true" id="cancel"></i>
    </label>
    <div class="sidebar">
        <header>My App</header>
        <ul>
            <li><RouterLink to="/music"><i class="fas fa-qrcode" aria-hidden="true"></i>Home</RouterLink></li>
            <li><a href="#"><i class="fas fa-link" aria-hidden="true"></i>Shortcuts</a></li>
            <li><a href="#"><i class="fas fa-stream" aria-hidden="true"></i>Overview</a></li>
            <li><a href="#"><i class="fas fa-calendar-week" aria-hidden="true"></i>Events</a></li>
            <li><a href="#"><i class="far fa-question-circle" aria-hidden="true"></i>About</a></li>
            <li><a href="#"><i class="fas fa-sliders-h" aria-hidden="true"></i>Services</a></li>
            <li><a href="#"><i class="far fa-envelope" aria-hidden="true"></i>Contact</a></li>
        </ul>
    </div>
    <section>
        <div class="d-flex justify-content-between ps-5">
            <div class="ps-5 ms-5 pt-2">
                <div class="text-center text-white" v-show="audio"><h1>List of Songs</h1></div>
                <div class="text-center text-white" v-show="list"><h1>Play List</h1></div>
            </div>
            <div class="pt-3">
                <button class="btn btn-warning mx-2 text-white" @click="getPopular">Popular</button>
                <button class="btn btn-info mx-2 text-white" @click="getNew">New</button>
            </div>
        </div>
        <div class="row ps-5">
            <div class="card m-2" style="width: 18rem;" v-for="(song,index) in allSongs" :key="index" >
                <img :src="song.cover" alt="" class="card-img-top" height="300">
                <div class="card-body">
                    <h4 class="card-title text-warning text-center">{{ song.title }}</h4>
                    <div v-show="audio">
                        <p class="card-text">{{ song.artist }}</p>
                        <p class="card-text">Duration: {{ song.duration }}</p>
                        <audio :src="song.audio" style="width: 230px;" controls></audio>
                    </div>
                    <div v-show="list">
                        <button class="btn btn-warning text-light" @click="playlist(index)">Show List</button>
                    </div>
                </div>
            </div>
        </div>
    </section>
</template>

<script>
    import axios from "axios";
    export default {
        data () {
            return {
                allSongs: [],
                audio: false,
                list: false,               
            }
        },
        mounted(){
            this.getPlaylist();
        },
        methods: {
            getPlaylist (){
                let url = 'https://musica-api.up.railway.app/playlist';
                axios.get(url).then((response)=>{
                    // console.log(response.data);
                    this.allSongs = response.data;
                    this.list = true
                    this.audio = false
                })
            },
            getNew (){
                let url = 'https://musica-api.up.railway.app/new';
                axios.get(url).then((res)=>{
                    this.allSongs = res.data;
                    this.audio = true
                    this.list = false
                })
            },
            getPopular (){
                let url = 'https://musica-api.up.railway.app/popular';
                axios.get(url).then((res)=>{
                    this.allSongs = res.data;
                    this.audio = true
                    this.list = false
                })
            },
            playlist(index){
                this.allSongs = this.allSongs[index].files;
                this.list = false
                this.audio = true
            },
        }
    }
</script>

<style>
</style>
