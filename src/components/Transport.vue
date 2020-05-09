<template>

<div class="row">
        <div @click="compute" class="col-xs-10 col-xs-offset-1 col-sm-10 col-sm-offset-1 col-md-10 col-md-offset-1">
            <div @click="isClicked = !isClicked"
            :class = "{isClickedStyle: isClicked, notIsClickedStyle: !isClicked}"  >
            <p> Transport:  <span> ${{value}}</span> </p>
                    
            </div>
           
        </div>
    </div>
    
</template>

<script>
export default {
    data(){
        return{
            value: 50,
            isClicked: false
        }
    },
    methods: {
        compute(){
            if (this.isClicked){
                this.$emit('addToTotal', this.value)
            }else{
                this.$emit('subtractFromTotal', this.value)
            }
        }
    }
    
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
.isClickedStyle{
    background-color: darkgreen;
    height: 65px;
    transition: 0.3s ease-in;
}
.notIsClickedStyle{
    background-color: palevioletred;
    height: 65px;
    color: black;
    transition: 0.3s ease-in;
}
p{
    padding: 10px;
    font-size: 25px;
    font-weight: bold;
}
.row :hover{
    cursor: pointer;
}
</style>