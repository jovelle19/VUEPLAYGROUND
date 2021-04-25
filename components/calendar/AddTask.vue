<template>
    <div class="calendar-task">
       <h3 class="todo-title"> TODO LIST </h3>

       <div class="todo-container">
            <h4 class=""> {{ dateselect.fulldate }} </h4>

            <input
            class="input-title"
            type="text"
            v-model="todoInput"
            placeholder="Add task here.."
            />

            <span v-if="!isEdit">
                <button class="btn-save" type="submit" v-on:click="addTodo()" >Save</button>
            </span>    
            <span v-else>
                <button class="btn-save"  type="submit" v-on:click="updateTodo()" >Update</button>
            </span>    
        </div>

        <div class="todo-container">
            <ul class="todo-items">
                <li v-for="(todoItem, index) in this.todoItems">
                   <p>{{ todoItem.date }} - {{ todoItem.title }} </p>

                   <button class="btn-edit" v-on:click="editTodo(index, todoItem)">Edit</button>
                   <button class="btn-delete" v-on:click="deleteTodo(index, todoItem)">Delete</button>
                </li>
            </ul>
        </div>
    </div>
</template>


<script>
    export default {
        props:["datedata", "dateselect"],
        data(){
            return {
                todoIndex:"",
                todoInput:"",
                todoItems:[],
                isEdit: false,
                todoAdded: false,
            }
        },
        methods:{
            addTodo(){
                this.todoItems.push({
                    date: this.dateselect.fulldate,
                    day: this.dateselect.day,
                    month: this.dateselect.month,
                    year: this.dateselect.year,
                    title: this.todoInput,
                });
                this.todoInput = "";
                this.todoAdded= true;

                this.$emit("addPin", this.todoItems);
            },
            editTodo(index, todo)
            {
                this.todoIndex = index;
                this.todoInput = todo.title;
                this.isEdit = true;
            },
            updateTodo()
            {
                this.todoItems.splice(this.todoIndex, 1);
                this.todoItems.push({
                    date: this.dateselect.fulldate,
                    day: this.dateselect.day,
                    month: this.dateselect.month,
                    year: this.dateselect.year,
                    title: this.todoInput,
                });

                this.isEdit = false;
                this.todoInput = "";
            },
            deleteTodo(index)
            {
                this.$emit("addPin", this.todoItems);
                this.todoItems.splice(index, 1);
            }
        }
        
    }
</script>



<style>
    .calendar-task{
        width: 700px;
        height:680px;
        padding: 5px;
        overflow: auto;
    }
    
    .todo-container{
        padding: 10px;
    }

    .input-title {
        margin-top: 10px;
        padding: 15px;
    }

    .btn-save{
        padding: 16px 25px;
        background: #00b000;
        color: white;
        border: none;
    }
    
    .btn-edit{
        margin: 2px 0;
        padding: 10px 20px;
        background: #0080c0;
        color: white;
        border: none;
    }

    
    .btn-delete{
        margin: 2px 0;
        padding: 10px 20px;
        background: #ff0000;
        color: white;
        border: none;
    }

    .todo-title{
        padding: 15px;
        font-size: 18px;
        font-weight: bold;
        background: #f4805e;
        color: white;
    }

    .todo-form{
        display: grid;
        grid-template-columns: repeat(2, 1fr);
    }

    .todo-items{
        display:inline-grid;
        padding: 4px 0;

    }
    
    .todo-items li{
        display: block;
        width: 100%;
        text-decoration: none;
        padding: 7px;
    }
    


</style>
