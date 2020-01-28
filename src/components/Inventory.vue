<template>
    <div class="row">

        <div v-for="(item,index) in items" :key="index" class="card" style="width: 18rem;">
            <img :src="item.photo" class="card-img-top" alt="...">
            <div class="card-body">
                <h5 class="card-title">{{item.title}}</h5>
                <p class="card-text">{{item.price}}</p>
                <a @click="addCart(item)" href="#" class="btn btn-primary">+Add</a>
            </div>


        </div>


    </div>
</template>


<script>

    export default {
        props: ['items'],
        methods:{
            addCart(item){
                this.$emit('newItemadded',item)
            }
        }
    }
</script>

<style>

</style>