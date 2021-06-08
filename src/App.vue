<template>
<div class="up">
  <toggle></toggle>
  </div>
  <h1>{{title}}</h1>
  <todo></todo>
  <div class="footer">
    <p class="this">Made with ❤ by Varun</p>
    <a href="https://github.com/vrun1208/To-do-App"  target="_blank" >
    <i class="fab fa-github"> </i> 
     </a> 
  </div>
</template>

<script>
import todo from './components/todo.vue'
import toggle from './components/toggle.vue'
export default {
  name: 'App',
  components: {
    todo,
    toggle,  
  },
  data(){
    return{
      title: "To-do App",
    }
  }, 

}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: left;
  margin-top: 10px;
  max-width: 600px;
	margin-left: auto;
	margin-right: auto;
	padding: 10px;
}

h1{
  font-family: Helvetica;
  font-weight: bolder;
  color: var(--text-color);

}
.up{
  margin-bottom: 50px;
}
.footer{
  display: flex;
  justify-content: center;
  position: fixed;
  left: 0;
  bottom: 0;
  width: 100%;
  background:var(--div-color);
}
p.this{
  font-style: normal;
  font-size: 9px;
  color: var(--text-color);
}
a{
  padding-left: 15px;
}
</style>
