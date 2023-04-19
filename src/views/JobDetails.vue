<template>
    <div class="about">
        <p>{{ id }}</p>
        <!-- <h1>This is an Jobs component</h1>
        <div v-for="job in jobs" :key="job.id">
            <h3>{{job.name}}</h3>
            <p>{{job.details}}</p>
            <p>{{job.company}}</p>
            <p>{{job.location}}</p>
            <p>{{job.salary}}</p>
            <p>{{job.type}}</p>
        </div> -->
    </div>
</template>

<script>
    export default {
        props: ['id'],
        data(){
            return {
                // id: this.$route.params.id,
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
