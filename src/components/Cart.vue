<template>
    <ul class="list-group">
        <li class="list-group-item">Item price</li>

        <li v-for="(item,index) in items" :key="index" class="list-group-item">
            <span><button class="btn btn-sm btn-danger" @click="removeItem(index)">x</button></span>
            $ {{item.price}}</li>

        <li class="list-group-item">Total price $ {{total}}</li>

    </ul>
</template>

<script>

    export default {
        props: ['items'],

        computed: {
            total() {
                var total = 0
                this.items.forEach(item => {
                    // eslint-disable-next-line no-console
                    var price = item.price
                    var parsed_price = Number(price.replace(/[^0-9.-]+/g, ""));
                    // eslint-disable-next-line no-console
                    console.log(parsed_price)
                    total = total + parsed_price
                })
                return total
            }
        },
        methods:{
            removeItem(index){
                this.$emit('itemRemoved',index)
            }
        }
    }
</script>

<style>

</style>