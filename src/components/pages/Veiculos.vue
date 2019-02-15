<template>
    <div id="veiculos">
        <b-container fluid class="vh-40 bg-full"
            :style="{ 'background-image': 'url(' + require('../../assets/img/img-car.jpg') + ')' }">
        </b-container>


        <b-container fluid class="vh-80 bg-color-1 pb-4">
                        
            <b-row>
           
                <b-col offset="2" cols="10">
                    <h2 class="color-2 mt-5">
                     Nossos veículos
                    </h2>
                </b-col>
                
                <b-col cols="2">
                    <b-list-group v-on:click="click">                    
                        <listItem v-on:veiculos="getVeiculos" v-for="marca in marcas"
                            v-bind:key="marca.marca" 
                            :marca="marca.marca"
                        />
                    </b-list-group>
                </b-col>
                
                <b-col cols="10">
                    <div v-show="show" class="text-center">
                        <b-progress :value="100" variant="success" class="mb-2" animated></b-progress>
                        <h2 class="color-2 mt-5">
                            Carregando...
                        </h2>
                    </div>
                    
                    <b-row>
                        <card v-for="veiculo in veiculos" v-bind:data="veiculo" v-bind:key="veiculo.idVeiculo" :veiculo="veiculo" />
                    </b-row>
                </b-col>

            </b-row>
            
        </b-container>
    </div>
</template>

<script>
import card from '../../components/shared/cards/CardPrinc.vue'
import listItem from '../../components/shared/cards/CardMarca.vue'

export default {

    components: {
        card,
        listItem
    },
    

    data() {
        return {
            show: false,
            marcas: [],
            veiculos: []
        };
    },

    created(){
        this.$http.get('https://artcarmultimarcas.herokuapp.com/list-marca')
        .then(res => res.json())
        .then(marcas => this.marcas = marcas, err => console.log(err));
    },

    methods:{
        click(){
            this.show = true;
            this.veiculos = [];
        },

        getVeiculos(v, a){
            this.veiculos = v;
            this.show = a;
        }
    }
}
</script>