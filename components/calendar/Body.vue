<template>
    <div>
       <ul class="calendar-dates">
            <li class="weeks" v-for="week in weeks">
                {{ week }}
            </li>
            <li class="calendar-blanks" v-for="blank in getFirstDay">
                {{ getFirstBlank + blank }}
            </li>
            <li v-for="days in getDaysInMonth"
                v-on:click="$emit('addtask', days, datedata.month, datedata.year)"
                class="datealign"
                :class = "{
                    calendarcurrentday:
                    days == dateToday &&
                    monthToday == datedata.month &&
                    yearToday == datedata.year,
                }
               ">
               {{ days }}

                <img src="~/assets/icon/pin.svg" v-for="todo in todos" class="date-pin" v-show="
                    todo.day == days &&
                    todo.month == datedata.month &&
                    todo.year == datedata.year
                ">


              

             </li>
            <li class="calendar-blanks" v-for="last in getLastBlank">
                {{ last }}
            </li>
       </ul>
    </div>
</template>


<script>
    import moment from "moment";

    export default {
        props: ["datedata","todos"],
        data(){
            return {
                weeks:[
                    "Sunday",
                    "Monday",
                    "Tuesday",
                    "Wednesday",
                    "Thursday",
                    "Friday",
                    "Saturday"
                ],
            };
        },
        computed: {
            getDaysInMonth(){
                return this.datedata.datehandler.daysInMonth();
            },
            getCurrentDate(){
                return this.datedata.datehandler.get("date");
            },
            getFirstDay(){
                var firstday = moment(this.datedata.datehandler).subtract(
                    this.getCurrentDate - 1,
                    "days"
                );
                return firstday.weekday();
            },
            getFirstBlank(){
                var lastmonth = moment(this.datedata.datehandler).subtract(
                    "1",
                    "month"
                );
               return lastmonth.daysInMonth() - this.getFirstDay;
            },
            getLastBlank(){
                return 42 - (this.getFirstDay + this.getDaysInMonth);
            },
            dateToday(){
                return this.datedata.datehandler.get("date");
            },
            monthToday(){
                return this.datedata.datehandler.format("MMMM");
            },
            yearToday(){
                return this.datedata.datehandler.format("Y");
            },
           
        },
    }
</script>


<style>
    .calendar-dates{
        display:grid;
        grid-template-columns: repeat(7, 1fr);
        grid-template-rows: 10%, (6, 1fr);
        text-align: center;
        list-style: none;
        border: 1px solid #dfdfdf;
    }
    .weeks{
        padding: 10px;
        font-weight:bold;
        align-items:center;
    }
    .calendar-dates{
        position:relative;
        padding: 10px;
    }
    .calendar-dates li {
        position: relative;
        border: 1px solid #7f7f7f;
        cursor: pointer;

    }
    .datealign
    {
        position: relative;
        display: flex;
        padding: 0 5px 70px 70px;
        flex-wrap: wrap;
    }
    .calendar-blanks{
        background: #e2e2e2 ;
        color: #696969;
        padding: 0 5px 70px 70px;
    }
    .calendarcurrentday{
        background: #0ec75c;
        color: white;
    }
    .date-pin{
        position:absolute;
        margin: 25px auto;
        width:20%;
    } 
    
</style>