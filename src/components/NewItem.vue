<template>
    <div>
        <form id="form" class="form-horizontal col-xs-10 col-xs-offset-1 col-sm-10 col-sm-offset-1 col-md-10 col-md-offset-1">
            <div class="form-group">
                <label for="inputEmail3" class=" col-xs-2 col-sm-2 control-label">Item</label>
                <div class="col-xs-10 col-sm-10">
                <input v-model="newItem.item" type="input" class="form-control" id="inputItem" placeholder="Item">
                </div>
            </div>
            <div class="form-group">
                <label for="inputPassword3" class=" col-xs-2 col-sm-2 control-label">Price</label>
                <div class="col-xs-10 col-sm-10">
                <input v-model.number= "newItem.price" type="number" class="form-control" id="inputPrice" placeholder="$">
                </div>
            </div>       
            <button @click.prevent="addNewItem" type="submit" class="btn btn-success">Add item</button>
        </form>
    </div>
</template>

<script>
export default {
    data(){
        return{
            newItem: {
                item: 'Food',
                price: 100,
            }

        }
    },
    methods: {
        addNewItem(){
            if ((this.newItem.item =='') || (this.newItem.price =='')){
                alert('Fill completely')
                // if any of the input field is empty
            }else{
            this.$emit('addNewItem', this.newItem)
            
            // this.$emit('addNewItem', this.item)
            }
        }
    }
}
</script>

<style scoped>
#form{
    border: 2px;
    margin-top: -5px;
    padding-top: 10px;
    padding-bottom: 10px;
    margin-bottom: 10px;
    background-color: rgba(56, 1, 95, 0.253);
}
</style>