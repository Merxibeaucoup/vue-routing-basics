<template>
<div v-if="job">
<h1>{{job.title}}</h1>
 <p> The job id is {{ job.id }}</p>

</div>

<div v-else>

<p>Loading job details......</p>
</div>


</template>

<script>
export default {
    props:['id'],
    
    data(){
        return{
            // to store the data fetched
           job: null
        }
    }, 
   mounted(){
        // using fetch API
        // this to reference the component
        // id is a prop
            fetch('http://localhost:3000/jobs/' + this.id)
            // get response of that url path
            .then((res)=> res.json())
            //populate the jobs array
            .then(data => this.job = data)
            // catch any erroe if any
            .catch(err => console.log(err.message))
    }

}
</script>

<style>

</style>