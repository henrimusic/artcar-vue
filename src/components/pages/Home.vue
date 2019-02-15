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
            img-width="1024px"
            img-height="480px"
            v-model="slide"
            @sliding-start="onSlideStart"
            @sliding-end="onSlideEnd"
          >
            <b-carousel-slide :img-src="require('../../assets/img/img-car.jpg')">
              <div class="content-slide right">
                <h1>Art Car a marca do seu carro</h1>
              </div>
            </b-carousel-slide>
            <b-carousel-slide :img-src="require('../../assets/img/automobile.jpg')">
              <h1>Vender carros é nossa arte</h1>
            </b-carousel-slide>
          </b-carousel>
          <div id="header-mb" class="bg-full vh-100 init-pad"
            :style="{ 'background-image': 'url(' + require('../../assets/img/img-car.jpg') + ')' }">
            <b-row>
              <b-col offset="1" cols="10">
                <h1 class="color-1 mt-5">Art Car Multimarcas</h1>
              </b-col>
              <b-col offset="1" cols="10">
                <p class="text-left color-1">
                  A marca do seu carro
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
             <card v-for="veiculo in veiculos" v-bind:data="veiculo" v-bind:key="veiculo.idVeiculo" :veiculo="veiculo" />
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