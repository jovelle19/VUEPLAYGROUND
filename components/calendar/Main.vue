<template>
    <div class="wrapper">

        <div class="calendar-main">
            <CalendarHeader v-bind:datedata="datedata" ></CalendarHeader>
            <CalendarBody   @addtask="adddetails"  v-bind:datedata="datedata"   v-bind:todos="todos"  ></CalendarBody>
        </div>

        <div class="calendar-main">
            <CalendarAddTask v-bind:datedata="datedata" v-bind:dateselect="dateselect" @addPin="addPin"></CalendarAddTask>
        </div>

    </div>
</template>


<script>
    import moment from "moment";
    import CalendarAddTask from "../../components/calendar/AddTask.vue";
    import CalendarHeader from "../../components/calendar/Header.vue";
    import CalendarBody from "../../components/calendar/Body.vue";

    export default {
        components:{
            CalendarBody,
            CalendarHeader,
            CalendarAddTask
        },
        data(){
            return{
                datedata: {
                    today: moment(),
                    datehandler: moment(),
                    year: "",
                    month: "",
                    day: ""
                },
                dateselect: {
                    fulldate: "",
                    year: "",
                    month: "",
                    day: "",
                },
                todos:[]
            }
        },
        methods:{
            adddetails(daySelect, monthSelect, yearSelect){
                this.dateselect.fulldate = monthSelect +"-"+ daySelect +"-"+ yearSelect;
                this.dateselect.year = yearSelect;
                this.dateselect.month = monthSelect;
                this.dateselect.day = daySelect;
            },
            addPin(todos){
                console.log(todos);
                this.todos = todos;
            }

        }
    }
</script>


<style>
    .wrapper{
        display:grid;
        grid-template-columns: repeat(2, 1fr);
    }
    .calendar-main{
        margin: 20px 50px;
        width:90%;
        border: 2px solid #dfdfdf;
        border-radius: 2px;
        box-sizing: border-box;
    }
</style>