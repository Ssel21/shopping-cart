 <template>
   <h1>My Cart</h1>
    <h3>Order Total Price: {{ 
        this.total == 0.00 ? '0.00' : this.total
       }} </h3>
  <div class="container" :key="order.id" v-for="order in myOrders"> 
      <Order :order="order"
        @delete-item="$emit('delete-item', order.id)"
        @update-orderQuantity="updateQuantity"
        @plus="$emit('plus', order)"
        @minus="$emit('minus', order)"
  
       />
  </div>
</template>

<script>

   import Order from "../Cart/Order"
export default {
 
name: "Orders",
props: {
    myOrders:Array,
    total:Number
}, 

components:{
    Order
},
methods: {
    updateQuantity: function(data, item){
        console.log(data);
        this.$emit('update-orderQuantity', data, item)
    }
},

emits:["update-orderQuantity", "delete-item","plus", "minus" ]
}
</script>

<style>

</style>