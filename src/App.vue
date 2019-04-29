<template>
  <div id="app">
  <h1>TODO
 <span calss="info">({{remaining.length}}/{{todos.length}})</span>
  </h1>

  <ul>
  <ToDoItem v-for="todo as todos" :todo="todo" @delete="deleteTodo">
  
  </ul>
  <form @submit.prevent="addTodo"> 
  <input type="text" v-model="newTodo">
  <input type="submit" value="Add">
  </form>

  </div>
</template>

<script>
import ToDoItem from "./components/ToDoItem.vue"

export default {
name:"app",
components:{
	ToDoItem
},
date(){
	return{
	todos:[
	{id:1,text:"abc",isDone:faulse},
	{id:2,text:"dcr",isDone:faulse}
],
newToDo:""
	}
},
methods:{
addTodo:function(){
	const newId = Math.max.apply(null,this.todos.map(t=>t.id))+1;
	this.todos.push({id:newId,text:this.newTodo,isDone:false});
	this.newTodo="";
	},
deleteTodo:function(todo){
	this.todos=this.todos.filter(item=>item!==todo);
}	
},
computed:{
	remaining:function(){
	return this.todos.filter(function(todo){
	return !todo.isDone;

	});
	}
}
}
</script>

<style>

</style>
