<template>

<small>{{item}}</small>
   
</template>

<script>
import axios from 'axios'
export default{
    data(){
        return{
            item:null
        }
    },
    mounted(){
        this.fetchItem()
    },
    methods:{
        fetchItem(){
               var self = this
                axios.get('http://localhost:3000/item/' + this.$route.params.id).then(response =>{
                    self.item = response.data
                })
            }
}
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
