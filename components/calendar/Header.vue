<template>
    <div class="calendar-header">
        <button @click="prevDate" class="btn-date"> < </button>
        <h4 >{{ dateDetails }}</h4>
        <button @click="nextDate" class="btn-date"> > </button>
    </div>
</template>


<script>
    import moment from "moment";

    export default {
        props: ["datedata"],

        computed:{
            year() {
               this.datedata.year = moment(this.datedata.datehandler).format('Y');
               return this.datedata.year;
            },
            month() {
                this.datedata.month = moment(this.datedata.datehandler).format('MMMM');
                return this.datedata.month;
            },
            date() {
                this.datedata.date = moment(this.datedata.datehandler).format('Do');
                return this.datedata.date;
            },
            dateDetails() {
                return this.month + ' - ' + this.date + ' - ' + this.year;
            }
        },
        methods:{
            prevDate() {
                this.datedata.datehandler = moment(this.datedata.datehandler).subtract(
                    "1",
                    "month"
                );
            },
            nextDate() {
                this.datedata.datehandler = moment(this.datedata.datehandler).add(
                    "1",
                    "month"
                )
            }
        }
       
    }
</script>


<style >

    .calendar-header{
        display: grid;
        grid-template-columns: repeat(3, 1fr);
        grid-column-gap: 10px;
        align-items:center;
        text-align: center;
    }
    .btn-date{
        padding: 15px;
        font-size: 18px;
        font-weight: bold;
        background: #f4805e;
        color: white;
        border: white 2px;
    }

</style>