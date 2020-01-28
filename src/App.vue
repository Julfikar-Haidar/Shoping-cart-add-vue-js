<template>
    <div id="app">
        <navbar @search="search"></navbar>

        <div class="container-fluid">
            <div class="row">
                <div class="col-md-9">

                    <Inventory @newItemadded="addcartItem" :items="items"></Inventory>

                </div>
                <div class="col-md-3">
                    <cart @itemRemoved="deleteItem" :items="cart"></cart>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
    // import HelloWorld from './components/HelloWorld.vue'
    import Navbar from './components/Navbar'
    import Cart from './components/Cart'
    import Inventory from './components/Inventory'
    import data from './data.js'

    export default {
        name: 'app',
        components: {
            Navbar,
            Cart,
            Inventory

        },
        data(){
        return {
            items:[],
            cart:[]
        }
        },
        mounted() {
            this.items=data;

        },
        methods:{
            search(keyword){
                this.items = data.filter(item => {
                return  item.title.toLowerCase().indexOf(keyword.toLowerCase()) !==-1
                })
            },
            addcartItem(item){
                this.cart.push(item);
            },
            deleteItem(index){
                this.cart.splice(index,1)
            }
        }
    }
</script>

<style>
    .container-fluid {
        padding-top: 10px;
    }
</style>
