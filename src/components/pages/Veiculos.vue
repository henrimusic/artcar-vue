<template>
    <div id="veiculos">
        <b-container fluid class="vh-40 bg-full"
            :style="{ 'background-image': 'url(' + require('../../assets/img/img-car.jpg') + ')' }">
        </b-container>


        <b-container fluid class="vh-80 bg-color-1 pb-4">
            
            <b-row>

                
                <b-col offset="1" cols="10">
                    <h2 class="color-2 mt-5">
                     Nossos veículos
                    </h2>
                </b-col>

                <b-col cols="2">
                    <b-list-group>
                        <listItem v-for="marca in marcas"
                            v-bind:key="marca.marca" 
                            :marca="marca.marca"
                             :quantidade="quantidade"/>
                    </b-list-group>
                </b-col>

                <b-col cols="8">
                    <b-row>
                        <!-- <card v-for="veiculo in veiculos" v-bind:data="veiculo" v-bind:key="veiculo.idVeiculo" :img="veiculo.base64" :tipo="veiculo.tipoVeiculo" :modelo="veiculo.modelo" :anoModelo="veiculo.anoModelo"/> -->
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
            marcas: [],
            quantidade: 1,
            counter : 0
        };
    },

    created(){
        this.$http.get('https://artcarmultimarcas.herokuapp.com/list-marca')
        .then(res => res.json())
        .then(marcas => this.marcas = marcas, err => console.log(err));
    },

    computed:{
        
    }

}
</script>