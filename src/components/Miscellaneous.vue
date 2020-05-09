<template>
    <div class="row">
        <div @click="compute" class="col-xs-10 col-xs-offset-1 col-sm-10 col-sm-offset-1 col-md-10 col-md-offset-1">
            <div @click="isClicked = !isClicked"
            :class = "{isClickedStyle: isClicked, isNotClickedStyle: !isClicked}"  >
            <p> Miscellaneous:  <span> ${{value}}</span> </p>
                    
            </div>
           
        </div>
        
    </div>
</template>

<script>

export default {
    data: function(){
        return{
            isClicked: false,
            value: 100
        }

    },
    methods:{
        compute(){
            if (this.isClicked){
                this.$emit('addToTotal', this.value)
            }else{
                this.$emit('subtractFromTotal', this.value)
            }
        }
    },
    props:['totalValue']
    // receives the data sent from app.vue instance
    
}
</script>
<style scoped>
.row{
    color: white;
    margin-bottom: 10px;
    text-align: left;
}
span{
    float: right;
}
p{
    padding: 10px;
    font-size: 25px;
    font-weight: bold;
}
.isClickedStyle {
    background-color: darkgreen;
    height: 65px;  
    transition: 0.3s ease-in;  
}
.isNotClickedStyle {
    background-color: palevioletred; 
    height: 65px;
    color: black;
    transition: 0.3s ease-in;

}
.row :hover{
    cursor: pointer;
}
</style>