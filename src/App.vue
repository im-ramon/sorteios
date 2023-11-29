<template>
    <div id="container">
        <div id="modal" v-if="modalAtivo" @click="fecharModal($event)">
            <div id="modal-area">
                <span class="fechar" @click="modalAtivo = false">x</span>
                <h1>
                    Você escolheu o número <u>{{ numeroEscolhido }}</u>
                </h1>
                <p>{{ textoAjuda }}</p>
                <p v-if="textoAjudaComplemetar !== '😘'"><br /><br />Clique no número para enviar uma mensagem.</p>
                <h1 class="textoAjudaComplemetar" v-html="textoAjudaComplemetar"></h1>
            </div>
        </div>
        <header>
            <div id="header-imagem">
                <img src="./assets/images/bike.jpg" alt="Bike" />
            </div>

            <div id="header-abertura">
                <h1>Bicicleta Aro 29</h1>
            </div>

            <div id="header-premio">
                <h2><span>Sorteio</span></h2>
                <h1>Dia 23/12/2023 (Federal)</h1>
            </div>

            <div id="header-exclicacao">
                <h2><span>Valor</span></h2>
                <h1>1 Dezena = <u>R$ 20,00</u></h1>
                <p>Escolha um número e envie uma mensagem avisando para o Whatsapp:</p>
                <h2>
                    <a href="https://api.whatsapp.com/send?phone=+5575982459849&text=Oi,%20escolhi%20um%20numero%20da%20do%20cha." target="_blank" rel="noopener noreferrer">(75) 9 8245-9849</a>
                </h2>
            </div>

            <div id="header-complemtos">
                <h2><span>Pix</span></h2>
                <h1>04021400524</h1>
                <span>(Leidiana Sena Souza)</span>
            </div>

        </header>

        <main>
            <div id="explicacao">
                <div id="item1">
                    <div></div>
                    <span>Números disponíveis</span>
                </div>

                <div id="item2">
                    <div></div>
                    <span>Números indisponíveis</span>
                </div>
            </div>
            <section id="numeros">
                <div class="numero" :class="item.disponivel ? 'disponivel' : 'indisponivel'" v-for="(item, index) in listaBilhetes" :key="index" @click="ativarModal(item.numero, item.disponivel, item.nome)">
                    <span id="nome-container">
                        {{ item.numero }}
                    </span>
                    <span v-if="item.disponivel != '1'" id="nome">
                        {{ item.nome }}
                    </span>
                </div>
            </section>
        </main>
    </div>
</template>

<script>
import data from '../data';

export default {
    data() {
        return {
            modalAtivo: false,
            listaBilhetes: data,
            textoAjuda: '',
            textoAjudaComplemetar: '',
            numeroEscolhido: '',
        };
    },
    methods: {
        ativarModal(numero, disponivel, nome) {
            if (disponivel) {
                this.textoAjuda = 'Agora basta enviar uma mensagem para o Whatsapp abaixo pedindo para reservarmos esse número.';
                this.textoAjudaComplemetar = `<a href="https://api.whatsapp.com/send?phone=+557575982459849&text=Oi,%20escolhi%20o%20número%20${numero}." target="_blank" rel="noopener noreferrer"> <span class="seta1">&#62;</span> (75) 9 8245-9849 <span class="seta2">&#60;</span> </a>`;
            } else {
                this.textoAjuda = `Desculpe! Esse número já foi escolhido por "${nome}", tente outro.`;
                this.textoAjudaComplemetar = '😘';
            }
            this.numeroEscolhido = numero;
            this.modalAtivo = true;
        },
        fecharModal(e) {
            if (e.target.id === 'modal') {
                this.modalAtivo = false;
            }
        },
    },
};
</script>
