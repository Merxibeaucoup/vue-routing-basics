<template>
  <nav>
    <router-link to="/">Home</router-link> |

    <!--- Same as router-link to="/about">About</!--router-link--->
        <router-link :to="{name: 'About'}">About</router-link> |

    <!--- Same as router-link to="/Jobs">Jobs</!--router-link--->
     <router-link :to="{name: 'Jobs'}">Jobs</router-link>
  </nav>

  <button @click="redirect">Redirect</button>

  <button @click="goBack">Go back</button>

  <button @click="goForward">Go forward</button>

  <router-view/>
</template>

<script>
export default {
  methods: {
    // navigates to a new directory using push method
    redirect(){
      // jumps to the Home page from wheerever we are 
      this.$router.push({name: 'Home'})
    },
    
    // uses go() method for number of jumps
    goBack(){
      // goes backward by 1
        this.$router.go(-1)
    },
        // uses go() method for number of jumps
    goForward(){
      //goes forward by 1
        this.$router.go(+1)
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

nav {
  padding: 30px;
}

nav a {
  font-weight: bold;
  color: #2c3e50;
}

nav a.router-link-exact-active {
  color: #42b983;
}

button{
  margin: 0 10px;
  padding: 10px;
  border-radius: 4px;
}
</style>
