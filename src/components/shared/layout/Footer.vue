<template>
<div>
    <div class="vh-20  bg-color-3">
        <b-container class="container">
            <b-row>
                <b-col sm="4">
                    <h5 class="h5-footer color-1">Sobre a Art Car</h5>
                    <p class="p-footer">Contamos com uma equipe especializada, com o foco em dar a melhor consultoria na hora de escolher seu sonhado veículo. Com duas concessionárias, em Suzano e outra em Mogi e 20 anos de experiência no mercado da região, confiança e transparência é a base de nosso relacionamento com você. Melhor atender e realizar seu sonho é a nossa arte.</p>
                </b-col>

                <b-col sm="4">
                    <h5 class="h5-footer color-1">Conteúdo do site</h5>
                    <router-link :to="{name: 'home'}" class="link"> > Página principal</router-link>
                    <br/><br/>
                    <router-link :to="{name: 'veiculos'}" class="link"> > Lista de veículos por marca</router-link>
                    <br/><br/>
                    <router-link :to="{name: 'contato'}" class="link"> > Entrar em contato</router-link>
                </b-col>

                <b-col sm="4">
                    <h5 class="h5-footer color-1">Parceria</h5>
                    <p class="p-footer" style="text-align: center"> 
                         
                        Dias Pimentel corretora de Seguros
                        
                    <img style="width:100px;" src="../../../assets/img/diaspimentel.png"/>
                    </p>
                </b-col>
            </b-row>
        </b-container>
    </div>
    <b-container fluid class="bg-color-4 p-2" style="text-align: center;">
        <b-row>
            <b-col>
                <p class="p-footer-2">©ARTCAR MULTIMARCAS</p>
            </b-col>
        </b-row>
    </b-container>
</div>
</template>