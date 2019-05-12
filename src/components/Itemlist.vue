<template>
    <div>
        Itemlist
        <div v-for="item in items" :key="item.name">
            <div class="item":class="{over500:item.price >=500}">
                <div class="name">名前:{{item.name}}</div>
                <div class="class">{{item.price}}円</div>
                <div v-if="item.price>=10000">高額商品</div>
            </div>
        </div>
        <div>
            <label for>
                名前
                <input type="text" v-model="newItemName">
            </label>
            <label for>
                価格
                <input type="number" v-model="newItemPrice">
            </label>
            <button @click="addItem">add</button>
        </div>
    </div>
</template>
<script>
export default{
    name:"Itemlist",
    data(){
        return{
            items:[
                {name:"りんご",price:100},
                {name:"たまご",price:160}
            ],
            newItemName:"",
            newItemPrice:0
        };
    },
    methods:{
        addItem(){
            this.items.push({name: this.newItemName, price:this.newItemPrice})
            
        }
    }
};
</script>

<style>
.over500{
    color:red
}
</style>