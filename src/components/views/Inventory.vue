<template>
    <div class="row">

        <div v-for="(item,index) in items" :key="index" class="card" style="width: 18rem;">
            <router-link :to="{path:'/item/' +item.id}"><img :src="item.photo" class="card-img-top" alt="..."></router-link>
            <div class="card-body">
                <router-link :to="{path:'/item/' +item.id}"><h5 class="card-title">{{item.title}}</h5></router-link>
                <p class="card-text">{{item.price}}</p>
                <a @click="addCart(item)" href="#" class="btn btn-primary">+Add</a>
            </div>


        </div>


    </div>
</template>


<script>
import axios from 'axios'
    export default {
        data(){
            return {
                items:[]
            }
        },
        mounted(){
            this.fetchInventory()
        },
        methods:{
            addCart(item){
                this.$emit('newItemadded',item)
            },
            fetchInventory(){
               var self = this
                axios.get('http://localhost:3000/items').then(response =>{
                    self.items = response.data;
                })
            }
        }
    }
</script>

<style>

</style>