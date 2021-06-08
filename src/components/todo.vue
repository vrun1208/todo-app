<template>
    <div class="form">
        <form @submit.prevent="addToDo">
		<label>Create Todo</label>
		<input type="text" v-model="adTodo" name="adTodo" placeholder="write something">
		<button type="submit">Add ToDo</button>
	</form>
    </div> 
    <div class="top">
        <h2>To-do List</h2>
    </div>
    
    <div>
        <ul>
            <li class="list" v-for="(todo,index) in lists" :key="index">
                    <span>{{todo.content}}</span>
                    <i class="fa fa-trash-alt" @click="deletedata(index)"></i>
            </li>
        </ul>
        <p v-if="lists.length === 0">no todos.</p>
    </div>
   
</template>

<script>
import {ref} from 'vue'
export default {
    setup(){
        const adTodo = ref('');
        const tododata = JSON.parse(localStorage.getItem('lists')) || [];
        //read items from the list
        const lists = ref(tododata);

        function addToDo(){
            if(adTodo.value){
                lists.value.push({
                    content: adTodo.value
                });
                adTodo.value = '';
            }
            savedata();
        }

        function savedata(){
            const sve = JSON.stringify(lists.value);
            localStorage.setItem('lists', sve);
            //add item to lists
        }
        function deletedata(index){
            lists.value.splice(index, 1);
            savedata()
        }

        return{
            lists,
            adTodo,
            addToDo,
            deletedata,
            savedata
        }
    }

}
</script>

<style>
.form{
    padding: 10px;
    border-radius: 6px;  
}
form{
    display: flex;
	flex-direction: column;
	width: 100%;
}
label{
    font-size: 14px;
	font-weight: bold;
}
input,button{
    padding-top: 10px ;
    padding-bottom: 10px;
    margin-top: 10px;
    margin-bottom: 10px;
    box-shadow: none;
    outline: none; 
    border-radius: 6px;
    font-size: 15px;
}
input{
    border: 2px none;
    color: initial;
}
button{
    cursor: pointer;
    background-color: #2196F3;
    border: 2px none;
}

.top{
    margin-top: 40px;
}
h2{
  font-family: Helvetica;
  font-weight: bolder;
  color: var(--text-color);
}
p{
  font-family: Helvetica;
  font-weight: lighter;
  color: var(--text-color);
  font-style: italic;
  text-align: center;
}
ul{
    padding: 5px;

}
li{
    display: flex;
    justify-content: space-between;
    align-items: center;
    list-style-type: none;
    padding: 6px;
    margin-bottom: 20px;
    border-radius: 6px;
}

</style>