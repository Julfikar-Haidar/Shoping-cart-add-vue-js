<template>
    <div id="app">
<!-- <router-link :to="{path: '/'}">Home</router-link> -->
<!-- <router-link :to="{path: '/test'}">test1</router-link>
<router-link :to="{path: '/test/1'}">tes2</router-link>
<router-link :to="{path: '/test/2'}">test3</router-link>
<router-link :to="{path: '/test/3'}">test4</router-link>  -->

        
       <navbar @search="search"></navbar>

        <div class="container-fluid">
           <div class="row">
                <div class="col-md-9">
               <router-view></router-view>
                   <!-- <Inventory @newItemadded="addcartItem" :items="items"></Inventory> -->

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
    // import Inventory from './components/Inventory'
    import data from './data.js'

    export default {
        name: 'app',
        components: {
            Navbar,
            Cart,
            // Inventory

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
