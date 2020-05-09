<template>
    <div class="container col-xs-10 col-xs-offset-1 col-md-8 col-md-offset-2 col-md-8 col-md-offset-2">
        <!-- <p> <span class="glyphicon glyphicon-plus" aria-hidden="false"></span> </p> -->
        
        <div class="row1">
            <button @click="addNewBtn=!addNewBtn" id="add" type="button" class="">
                +
            </button> <br>  
            <appNewItem v-if="addNewBtn" @addNewItem="addNewItem($event)"></appNewItem>          
                <h1>Expenses</h1>
                <appMiscellaneous
                    @addToTotal="addToTotal($event)"
                    @subtractFromTotal ="subtractFromTotal($event)"></appMiscellaneous>
                <appTransport
                    @addToTotal="addToTotal($event)"
                    @subtractFromTotal ="subtractFromTotal($event)">
                    
                </appTransport>
                <appslot v-for="(price, index) in newPrice"
                            :newVal = price
                            @addToTotal="addToTotal($event)"
                            @subtractFromTotal ="subtractFromTotal($event)"
                            
                            >
                 <p>{{ newItem[index] }}: <span> ${{price}} </span> </p>
                 <!--v-for="(price, index) in newPrice"
                     loops through newprice and uses the index value for
                     price to get the value of newItem array 
                     // :newVal = price// the current value of price is sent as a prop to slot.vue
                     -->
                </appslot>
                <div class="col-xs-10 col-xs-offset-1 col-sm-10 col-sm-offset-1 col-md-10 col-md-offset-1 total">
                    <hr>
                    <h2>Total: $ {{total}}</h2>
                </div>
                    
        </div>  
    </div>

</template>

<script>
import Miscellaneous from './components/Miscellaneous.vue'
import Transport from './components/Transport.vue'
import newItem from './components/NewItem.vue'
import slot from './components/Slot.vue'


export default {
    data: function(){
        return{
            total: 0,
            newPrice: [],
            newItem: [],
            addNewBtn: false
            // condition for the add new tab to be shown    
        }

    },
    methods:{
        addToTotal(value){
            this.total += value;
            // adds the content of total with the new value
        },
        subtractFromTotal(value){
            this.total -= value;
        },
        addNewItem(object){

            this.newPrice.push(object.price);
            // gets the object and pushes the price value to newPrice
            
            this.newItem.push(object.item);
            // console.log(object.price)
            // console.log(object.item)
            // this.newItem = object;
        }
    },
    components:{
        appMiscellaneous: Miscellaneous,
        appTransport: Transport,
        appNewItem: newItem,
        appslot: slot
    }
    
}
</script>
<style scoped>
.container{
    text-align: center;
    color: white;
}
.row1{
    display: inline-block;
    min-width: 550px;
    background-color:rgb(5, 5, 61);
    margin-top: 50px;   
}
.total{
    padding: 0px;
}
h1{
    padding: 20px;
    text-decoration: underline;
    font-style: italic;
}
h2{
    float: left;
    margin-top: -10px;
}
#add{
    float: right;
    margin: 10px;
    font-size: 15px;
    font-weight: bolder;
    height: 30px;
    width: 30px;
    color: white;
    background-color: green;
    border: none;
    border-radius: 5px;
}


</style>