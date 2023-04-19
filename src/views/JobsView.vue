<template>
    <div class="about">
        <h1>This is an Jobs component</h1>
        <div v-for="job in jobs" :key="job.id">
            <RouterLink :to="'/jobs/' + job.id">
                <h3>{{job.name}}</h3>
            </RouterLink>
        </div>
        <div class="d-flex">
            <button class="btn btn-info" @click="redirect">Redirect</button>
            <button class="btn btn-info" @click="back">Previous</button>
            <button class="btn btn-info" @click="next">Next</button>
        </div>
    </div>
</template>

<script>
    export default {
        data(){
            return {
                jobs: [
                    {name: 'Software developer', id:1, details: 'Fullstack software developer', company: 'Google', location: 'London', salary: '£50,000', type: 'Full time'},
                    {name: 'Data scientist', id:2, details: 'Google certified data scientist', company: 'Google', location: 'London', salary: '£50,000', type: 'Full time'},
                    {name: 'Designer', id:3, details: 'Graphics designer', company: 'Google', location: 'London', salary: '£50,000', type: 'Full time'},
                ]
            }
        },
        methods: {
            redirect(){
                this.$router.push('/jobs/1')
            },
            back(){
                this.$router.go(-1)
            },
            next(){
                this.$router.go(1)
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
