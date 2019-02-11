<template>
    <b-list-group-item href="#" :id="marca" v-on:click="log($event.target.id)" class="d-flex justify-content-between align-items-center">
        {{ marca }}
    </b-list-group-item>
</template>


<script>
export default {

    data(){
        return{

        }
    },
    
    methods:{
        log: function(id){
            this.$http.get('https://artcarmultimarcas.herokuapp.com/list-marca/'+id)
            .then(res => res.json())
            .then(veiculos => this.$emit('veiculos', veiculos), err => console.log(err));
        }
    },

    props:['marca']

}
</script>