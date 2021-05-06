<template>
     <h1>Menu</h1>
     <br />
     <br />
      <div :key="item.id" v-for="item in items">
       <Item     
       @add-item="$emit('add-item', item)"
        :item="item" />
    </div>
</template>
<script>
import Item from "../components/Item"

export default {
  name : "Items",
  props: {
    items : Array
  },
  components: {
      Item
  },
  emits:['add-item']
  
}
</script>
<style scoped>

</style>