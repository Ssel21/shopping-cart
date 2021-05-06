<template>
<div class="container">
  <Header  />
  <div class="row">
    <div class="column">
      <Items  @add-item="addOrder"  :items="items" />
    </div>
    <div class="column">
      <Orders :myOrders="myOrders" @delete-item="deleteItem" @update-orderQuantity="updateQuantity" 
      :quantity="quantity" @plus="increaseQuantity" @minus="decreaseQuantity" :total="total"/>
    </div> 
  </div>
</div>
</template>

<script >
import { Options, Vue } from "vue-class-component";
import Header from "../components/Header";
import Items from "../components/Items";
import Orders from "../components/Cart/Orders"
@Options({

  components: {
    Header,
     Items,
     Orders
  },
  data() {
    return {
      items : [],
      myOrders: [],
      exists: false,
      quantity: Number,
      total:Number
    }
  }, 
  methods:{
  itemExists(item){
     this.myOrders.map((order) => 
    { 
     if(item.id === order.id ){
        this.exists = true;
        this.total = this.total + item.price;
  
        return { ...order, orderQuantity: order.orderQuantity++};
    }else{
        this.exists = false;
    }
    });
        console.log(this.exists)
    if(!this.exists){
      item.orderQuantity =  1;
      this.myOrders = [...this.myOrders, item];
     this.total = this.total + (item.orderQuantity * item.price)
  
    }

  },  
  addOrder(item){
      this.itemExists(item);
      console.log(this.myOrders)
  },
  updateQuantity :function (data, item){
    this.myOrders = this.myOrders.map( i => i.id === item.id ? {...i, orderQuantity: data } : i);
   console.log(this.myOrders);
    this.total = 0;
   this.myOrders.map( o => this.total = this.total + (o.orderQuantity * o.price));
  },
  deleteItem(id){
   
    this.myOrders = this.myOrders.filter( item => item.id !== id);
    this.myOrders.forEach(element => {
      this.total = 0.00;
      this.total = element.orderQuantity * element.price;
    });
  },
  increaseQuantity(item){
    console.log(item)
     this.myOrders = this.myOrders.map( a => a.id === item.id  ? {...a, orderQuantity: a.orderQuantity + 1 } : a);
   const increased = item.orderQuantity + 1;
        this.total = this.total + item.price;
  },
    decreaseQuantity(item){

        if(item.orderQuantity === 1){
          alert("Actsion not allowed!")
        }else{
          this.myOrders = this.myOrders.map( x => 
          {  
     if(x.id === item.id ){ 
        return {...x, orderQuantity: x.orderQuantity - 1 }
     }else{
       return x;
     }}); 
      this.total = this.total - (1 * item.price);
        }
        
       
  },
  },

  created(){
    this.items = [{
       id:0,
      name: "Candy1",
      description: "sweets and candy",
      price: 20.00,
      quantity:100,
      orderQuantity :0
    },{
      id :1,
      name: "Candy2",
      description: "sweets and candy",
      price: 30.00,
      quantity:20,
       orderQuantity :0
    },
    {
      id:2,
      name: "Candy3",
      description: "sweets and candy",
      price: 40.00,
      quantity:0,
       orderQuantity :0
    }],
    this.total = 0.00;
  },


})
export default class Home extends Vue {}
</script>
<style scoped>
.column {
  float: left;
  width: 50%;
}
</style>
