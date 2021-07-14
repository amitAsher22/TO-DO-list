<template>
  <div class="main-ToDo"  >
    <h3 class="title" >To-Do List</h3>
    <div class="All-Todos" v-if="boolean" >
      <div  v-for="todo in toDos" :key="todo + 'w'">
        <p class="sentences">{{todo}}</p>
      </div>
      <button class="clear" @click="clearAll">Clear All</button>
    </div>

    <input type="text" placeholder="Add New To-Do" v-model="newList">
    <button class="add" @click="addToList"  >Add</button>
   

    <div class="instructions">
    <strong>instructions:</strong>
      <ul v-for="sentence in listOfInstructions" :key="sentence">
        <li>{{sentence}}</li>
      </ul>


    </div>
  </div>

</template>

<script>
export default {
  name: "TODo",
  data(){
    return{
      listOfInstructions:["Click the To-Do list text to toggle between done/undone" , "use clear all button to remove all items" , "use the input field to add new to-dos"],
      newList:'',
      boolean:false,
      toDos:[],
    
     


    }
  },
  methods:{
    addToList:function (){
      if(!this.boolean && this.newList  ){
        this.boolean = !this.boolean
      }
      this.toDos.push(this.newList)
      localStorage.setItem('todo' , JSON.stringify(this.toDos))
      this.newList =''
    },
    clearAll:function (){
      this.toDos =[]
      this.boolean = false
    }
  },
  created() {
    this.toDos = localStorage.getItem("todo") ? JSON.parse(localStorage.getItem("todo")) : this.toDos
  }
}
</script>

<style scoped>
body{
  font-family: 'Forum', cursive;
}
.main-ToDo{
  background-color: rgba(248, 247, 247, 0.79);
  border: 1px solid ;
  width: 30%;
  height: 80%;
  margin:  10px auto;
  padding: 20px;
}
.add{
  background-color: #3737f3;
  color: white;
  border: none;
  padding: 5px;
  border-radius: 2px;
  margin-left: 3px;
}
.add:hover{
  color: black;
}
.clear{
  background-color: #990e2e;
  border: none;
  border-radius: 2px;
  padding: 4px;
  color: white;
  margin-bottom: 10px;
}
.clear:hover{
  color: black;
}
.sentences{
  color: black;
  font-weight: lighter;
}
.instructions{
  margin-top: 10%;
  color: rgb(160, 158, 158);
}
ul{
  margin-bottom: 0;
}
input{
  width: 50%;
}
.title{
  font-weight: bolder;
}



</style>