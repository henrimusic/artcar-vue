<template>
    <div id="contato">
        <b-container fluid class="vh-40 bg-full"
            :style="{ 'background-image': 'url(' + require('../../assets/img/automobile-cars-headlights-120049.jpg') + ')' }"
        >
        </b-container>
        <b-container>
            <b-row>
                <b-col cols=12>
                    <h2 class="color-2 mt-5 mb-4">
                        Entre em Contato
                    </h2>
                </b-col>
                <div class="w-100 mt-5"></div>
                <b-col md="3" class="p-5">
                    <p class="color-2 text-justify mt-4">
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
                    </p>
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
                                <p>
                                    Preencha nossa ficha de financiamento e agilize o seu processo de compra. Fotografe ou digitalize o formulário preenchido e envie para o nosso Whats +55 11 97040-8908!
                                </p> 

                                <br/>

                                <a href="../../src/assets/ficha.pdf" download="ficha de financiamento">
                                    <b-button variant="primary">Ficha de Financiamento
                                    </b-button>
                                </a>

                                <br/> 
                                
                                <!-- <b-form-group
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
                                    label="Ficha de financiamento"
                                    label-for="ficha"
                                    class="mt-3"
                                >
                                    <b-form-file id="ficha"
                                        placeholder="Selecione seu pdf preenchido"
                                        accept=".pdf"
                                        @change="upload"
                                        ref="fileinput"
                                        required
                                        >
                                    </b-form-file>
                                    
                                </b-form-group> -->


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
                email: '',
                file: null
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
            if (this.form.assunto == '') {
                this.form.assunto = 'Ficha de financiamento';
                
                console.log(this.form);

                this.$http.post('https://artcarmultimarcas.herokuapp.com/contato', this.form).then(() => this.form = {
                    msg: '',
                    assunto: '',
                    email: '',
                    file: null
                }, err => console.log(err));
    
                this.$refs.fileinput.reset();

            } else {
                
                console.log(this.form);

                this.$http.post('https://artcarmultimarcas.herokuapp.com/contato', this.form).then(() => this.form = {
                    msg: '',
                    assunto: '',
                    email: '',
                    file: null
                }, err => console.log(err));
            }
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

