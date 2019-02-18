<template>
    <b-col cols="8" sm="8" md="6" lg="3" class="mt-5 d-flex align-content-center justify-content-center">
        <div class="card-prin" @click="pushInterna(veiculo.idVeiculo)">
            <div class="bg-full"
                :style="{'background-image': 'url( data:image/png;base64,' + veiculo.base64 + ')'}">
            </div>
            <div class="body">
                <h5 class="color-3">{{ veiculo.modelo }}  {{ veiculo.versao }}</h5>
                <hr>
                <div class="w-100 d-flex align-content-center justify-content-center">
                    <div class="price bg-color-3">
                        <p class="color-1">{{ veiculo.anoModelo }}</p>
                    </div>
                </div>
                
            </div>
        </div>
    </b-col>
</template>


<script>
export default {

    props: {
        veiculo: {
            required: true,
            type: Object
        },
    },

    methods: {
        pushInterna(id){
            this.$router.push({ name: 'veiculo-interna', params: { id: this.veiculo.idVeiculo } });
        }
    }

}
</script>