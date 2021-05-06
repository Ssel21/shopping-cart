<template>
  <div class="order"> 
      
       <h4 class="orderName">{{order.name}}</h4>
        <h6>{{order.description}}</h6>
        <h5 class="price">Price : {{order.price.toFixed(2)}}</h5> 
        <input v-bind:value="order.orderQuantity"   v-on:input="updateOrder($event.target.value, order)"/>
       
        <button ><i   class="fas fa-plus" @click="$emit('plus', order)"></i> </button>
        <button @click="$emit('minus', order)"><i   class="fas fa-minus" ></i> </button>    
       <button class="delete" @click="$emit('delete-item', order.id)"><i   class="fas fa-times" ></i> Remove from Cart</button>
        <br/>
        <small>Total Price:{{order.orderQuantity * order.price}} </small>
  </div>
</template>

<script>
export default {
name:"Order",
 props: {
        order: Object,
        quantity:Number
    },
 methods:{
        updateOrder :function(value, item){
            console.log(value)
             this.$emit('update-orderQuantity',  value, item)

        }
    },


}
</script>

<style scoped>
div{
    
    background: lightblue;
    border: 3px solid lightseagreen;
    margin: 5px;
   padding: 0;
    cursor: pointer;
    width: 500px;
    border-radius: 20px;
    
}
button, input{
    margin-left: 3px;
    margin-bottom: 20px;
    padding: 2px;
    border: 2px solid lightseagreen;
    
}
.fa-plus, .fa-minus{
        color: steelblue;

}
.fa-times{
    color: steelblue;

}
.delete{
    margin-top: 10px;
    
    padding: 4px;
    border-radius: 5px;

}
.price {
   font-weight: 800;

}
</style>