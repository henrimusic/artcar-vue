<template>
    <div id="contato">
        <b-container fluid class="vh-40 bg-full"
            :style="{ 'background-image': 'url(' + require('../../assets/img/automobile.jpg') + ')' }"
        >
        </b-container>
        <b-container>
            <b-row>
                <b-col cols=12>
                    <h2 class="color-2 mt-5 mb-4">
                        Entre em Contato
                    </h2>
                </b-col>
                <b-col md="3" class="p-5">
                    <b-row><p class="color-3 text-left">
                        <svg width="30" version="1.1" xmlns="http://www.w3.org/2000/svg" height="30" viewBox="0 0 64 64" xmlns:xlink="http://www.w3.org/1999/xlink" enable-background="new 0 0 64 64">
                            <g>
                                <g fill="#1D1D1B">
                                <path d="M32,0C14.355,0,0,14.355,0,32s14.355,32,32,32s32-14.355,32-32S49.645,0,32,0z M32,60    C16.561,60,4,47.439,4,32S16.561,4,32,4s28,12.561,28,28S47.439,60,32,60z"/>
                                <circle cx="20.518" cy="21.361" r="4.338"/>
                                <circle cx="43.48" cy="21.361" r="4.338"/>
                                <path d="m52.541,36.568c-1.053-0.316-2.172,0.287-2.488,1.344-0.035,0.119-3.739,11.947-18.053,11.947-14.219,0-17.904-11.467-18.055-11.955-0.32-1.055-1.441-1.65-2.486-1.336-1.059,0.317-1.66,1.432-1.344,2.489 0.045,0.148 4.627,14.802 21.885,14.802s21.84-14.654 21.885-14.803c0.316-1.056-0.285-2.171-1.344-2.488z"/>
                                </g>
                            </g>
                        </svg>
                        Mande sua dúvida ou sugestão, vamos ficar felizes em esclarecer qualquer coisa!
                    </p></b-row>
                    
                    <b-row><p class="color-3 text-justify mt-4" style="text-align: center;">
                        <svg version="1.1" id="Layer_1" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" x="0px" y="0px"
                            width="30" height="30" viewBox="0 0 512 512" enable-background="new 0 0 512 512" xml:space="preserve">
                        <path fill="#1D1D1B" stroke="#1D1D1B" stroke-width="12" stroke-linejoin="round" stroke-miterlimit="10" d="M357.929,296.145
                            l-48.617,48.9l24.145,24.133c0,0-59.938-14-120.485-74.254c-49.488-49.489-69.788-96.002-70.398-116.596l20.3,20.271l48.9-48.612
                            L89.805,28.016L41.188,76.943l0.905,0.876C10.462,129.134,57.88,247.822,159.005,348.912
                            c107.639,107.684,223.352,166.422,271.991,117.816l48.617-48.605L357.929,296.145z"/>
                        </svg>
                        Telefone
                        <br/>
                        (11) 4747-3202 - Suzano
                        <br/>
                        (11) 4722-7995 - Mogi
                    </p></b-row>


                    

                    <b-row><p class="color-3 text-left mt-4" style="text-align: center;">
                        <svg version="1.1" id="Layer_1" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" x="0px" y="0px"
                            width="30" height="30" viewBox="0 0 512 512" enable-background="new 0 0 512 512" xml:space="preserve">
                        <path d="M256,4c-78.509,0-142.154,63.644-142.154,142.154S256,508,256,508s142.154-283.337,142.154-361.846S334.509,4,256,4z
                            M256,246.308c-53.529,0-96.923-43.394-96.923-96.923S202.471,52.462,256,52.462s96.923,43.394,96.923,96.923
                            S309.529,246.308,256,246.308z"/>
                        </svg>
                        Endereço
                        <br/>
                        Loja 1 - Av. Brasil, 1301 Jd. Monte Cristo - Suzano - SP
                        <br/>
                        Loja 2 - R. Guilherme George, 2336 Jundiapeba - Mogi das Cruzes - SP
                    </p></b-row>

                    
                </b-col>
                <b-col md="8" offset-md="1">
                    <b-row>
                        <b-col sm="11" class="form">
                            <div class="w-100">
                                <p class="color-3">Qual o motivo do seu contato?</p>
                                <div class="btn-toggle">
                                    <div id="tirarDuvidasBtn" class="active" @click="handlerFormRender(1)">Tirar dúvidas</div>
                                    <div id="tirarAdiantarBtn" @click="handlerFormRender(2)">Adiantar Compra</div>
                                </div>
                            </div>

                            <div v-if="simpleForm">
                                <b-form-group
                                    label="Endereço de e-mail"
                                    label-for="email"
                                    description="A partir deste e-mail que iremos entrar em contato."
                                    class="mt-3"
                                >
                                    <b-form-input id="email"
                                        type="email"
                                        required
                                        placeholder="Escreva seu e-mail"
                                        v-model="form.email"
                                    >
                                    </b-form-input>
                                </b-form-group>
                                <b-form-group
                                    label="Assunto do contato"
                                    label-for="assunto"
                                >
                                    <b-form-input id="assunto"
                                        type="text"
                                        required
                                        placeholder="Conte o motivo do seu contato"
                                        v-model="form.assunto"
                                    >
                                    </b-form-input>
                                </b-form-group>
                                <b-form-group
                                    label="Mensagem"
                                    label-for="mensagem"
                                >
                                    <b-form-textarea id="mensagem"
                                        placeholder="Escreva sua mensagem"
                                        :rows="6"
                                        v-model="form.msg"
                                    >
                                    </b-form-textarea>
                                </b-form-group>
                                
                            <b-button class="mt-3" size="lg" @click="sendForm()">Enviar</b-button>
                            </div>


                            <div v-if="!simpleForm">
                                <br/>
                                <p class="color-2 text-justify mt-4">
                                    Preencha nossa ficha de financiamento e agilize o seu processo de compra. Fotografe ou digitalize o formulário preenchido e envie para o nosso Whats +55 11 97040-8908!
                                </p> 

                                <br/>
                                <a :href="require('../../assets/pdf/ficha.pdf')" download="ficha de financiamento">
                                    <b-button variant="primary">Ficha de Financiamento
                                    </b-button>
                                </a>
                                <br/> 
                            </div>

                        </b-col>
                    </b-row>
                </b-col>
                <div class="w-100 mt-5"></div>
            </b-row>
        </b-container>
    </div>
</template>


<script>
export default {

    data() {
        return {
            simpleForm: true,
            form: {
                msg: '',
                assunto: '',
                email: ''
            }
        }
    },
    

    created(){
        window.scrollTo(0, 0);
    },

    methods: {

        upload(e){
            e.preventDefault();
            this.form.file = e.target.files[0];
            console.log(this.form.file);
        },


        sendForm() {
            this.$http.post('https://artcarmultimarcas.herokuapp.com/contato', this.form).then(() => this.form = {
                msg: '',
                assunto: '',
                email: ''
            }, err => console.log(err));
        },
        


        handlerFormRender(decider){
            if (decider < 2) {
                this.simpleForm = true
                document.getElementById('tirarDuvidasBtn').classList.add('active');
                document.getElementById('tirarAdiantarBtn').classList.remove('active');
            } else {
                this.simpleForm = false
                document.getElementById('tirarAdiantarBtn').classList.add('active');
                document.getElementById('tirarDuvidasBtn').classList.remove('active');
            }
        }
        
    }
}
</script>

