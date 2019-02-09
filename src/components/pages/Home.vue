<template>
  <div id="home">
    <b-container fluid class="vh-90 no-padding bg-full">
      <b-row class="no-margin">
        <b-col cols="12" class="no-padding">
          <b-carousel
            id="carousel"
            style="text-shadow: 1px 1px 2px #333;"
            indicators
            :interval="3000"
            img-width="100%"
            v-model="slide"
            @sliding-start="onSlideStart"
            @sliding-end="onSlideEnd"
          >
            <b-carousel-slide :img-src="require('../../assets/img/img-car.jpg')">
              <div class="content-slide right">
                <h1 class="color-1">ArtCar</h1>
                <p class="text-left">Contamos com uma equipe especializada, com o foco em dar a melhor consultoria na hora de escolher seu sonhado veículo. Com duas concessionárias, em Suzano e outra em Mogi e 20 anos de experiência no mercado da região, confiança e transparência é a base de nosso relacionamento com você. Melhor atender e realizar seu sonho é a nossa arte.</p>
              </div>
            </b-carousel-slide>
            <b-carousel-slide :img-src="require('../../assets/img/automobile-cars-headlights-120049.jpg')">
              <h1>Vender carros é nossa arte</h1>
            </b-carousel-slide>
          </b-carousel>
          <div id="header-mb" class="bg-full vh-100 init-pad"
            :style="{ 'background-image': 'url(' + require('../../assets/img/img-car.jpg') + ')' }">
            <b-row>
              <b-col offset="1" cols="10">
                <h1 class="color-1 mt-5">ArtCar</h1>
              </b-col>
              <b-col offset="1" cols="10">
                <p class="text-left color-1">
                  Contamos com uma equipe especializada, com o foco em dar a melhor consultoria na hora de escolher seu sonhado veículo. Com duas concessionárias, em Suzano e outra em Mogi e 20 anos de experiência no mercado da região, confiança e transparência é a base de nosso relacionamento com você. Melhor atender e realizar seu sonho é a nossa arte.
                </p>
              </b-col>
              </b-row>
          </div>
        </b-col>
      </b-row>
    </b-container>
    <b-container fluid class="vh-80 bg-color-1 pb-4">
      <b-row>
        <b-col offset="1" cols="10">
            <h2 v-if="show" class="color-3 mt-5">
              Carregando veículos...
            </h2>
            <h2 v-else="" class="color-3 mt-5">
              Podem chamar sua atenção!
            </h2>
        </b-col>
        <b-col cols="12">
          <b-progress v-show="show" :value="value" variant="success" class="mb-2" animated></b-progress>
          <b-row>
            <card v-for="veiculo in veiculos" v-bind:data="veiculo" v-bind:key="veiculo.idVeiculo" :img="veiculo.base64" :tipo="veiculo.tipoVeiculo" :modelo="veiculo.modelo" :anoModelo="veiculo.anoModelo"/>
          </b-row>
        </b-col>
      </b-row>
    </b-container>
  </div>
</template>

<script>
import card from '../../components/shared/cards/CardPrinc.vue'

export default {

  components: {
    card
  },

  data() {
    return {
      slide: 0,
      sliding: null,
      veiculos: [],
      value: 100,
      show: true
    };
  },
    
  created(){
    this.$http.get('https://artcarmultimarcas.herokuapp.com/list-home')
    .then(res => res.json())
    .then(function (veiculos){
        this.veiculos = veiculos
        this.show = false
    }, err => console.log(err));
  },

  methods: {
    onSlideStart(slide) {
      this.sliding = true;
    },
    onSlideEnd(slide) {
      this.sliding = false;
    }
  }
};
</script>