<template>
    <div class="item">
         <h4 class="itemName">{{item.name}}</h4>
        <h6>{{item.description}}</h6>
        <h5 class="price">Price : {{item.price.toFixed(2)}}</h5>       
        <button class="cart" @click="$emit('add-item', item)"><i   class="fas fa-cart-plus" ></i> Add to Cart</button>
    </div>
</template>

<script>


export default {
    name: "Item",
    props: {
        item: Object
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
    margin-left: 150px ;
}

.fa-minus{
color: red;
   padding: 5px;
}
.fa-plus{
color: lightseagreen;
   padding: 5px;
}

.price {
   font-weight: 800;

}
.orderNo{
    display: inline-block;
    padding: 5px;
}
button{
    margin-bottom: 40px;
    padding: 8px;
    border-radius: 5px;
    border: 2px solid lightseagreen;
 
}
.fa-cart-plus{
color: steelblue;
}

</style>
