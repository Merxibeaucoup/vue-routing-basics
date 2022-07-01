<template>
<h1> Jobs </h1>

<!--- always use a key property when we used v-for --->
<div v-if="jobs.length">
        <div v-for="job in jobs" :key="job.id" class="job"> 
        <router-link :to="{name: 'JobDetails', params: {id: job.id}}"> 

                <h2>{{ job.title }}</h2>

        </router-link>
        </div>
  </div>
  <div v-else>
    <p>Loading jobs.....</p>
  </div>
</template>

<script>
export default {
    data(){
        return{
            jobs:[]
        }
    },
    // fetch data
    mounted(){
        // using fetch API
            fetch('http://localhost:3000/jobs')
            // get response of that url path
            .then((res)=> res.json())
            //populate the jobs array
            .then(data => this.jobs = data)
            // catch any erroe if any
            .catch(err => console.log(err.message))
    }

}
</script>

<style>

.job h2{
    background: #f4f4f4;
    padding: 20px;
    border-radius: 10px;
    min-width: 600px;
    cursor: pointer;
    color: #444;
}
.job h2:hover{
    background: #ddd;
}
.job a{
    text-decoration: none;
}
</style>