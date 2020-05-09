<template>
    <div class="row">
        <div @click="compute" class="col-xs-10 col-xs-offset-1 col-sm-10 col-sm-offset-1 col-md-10 col-md-offset-1">
            <div @click="isClicked = !isClicked"
            :class = "{isClickedStyle: isClicked, isNotClickedStyle: !isClicked}"  >
            <slot></slot>
                    
            </div>
           
        </div>
        
    </div>
</template>

<script>

export default {
    data: function(){
        return{
            isClicked: false
        }

    },
    methods:{
        compute(){
            if (this.isClicked){
                this.$emit('addToTotal', this.newVal)
                // alert(this.newVal)
            }else{
                this.$emit('subtractFromTotal', this.newVal)
                // alert('unclicked')
                // alert(this.newVal)
            }
        }
    },
    props:['newVal']
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