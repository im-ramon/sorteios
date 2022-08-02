<template>
  <div id="container">
    <div id="modal" v-if="modalAtivo" @click="fecharModal($event)">
      <div id="modal-area">
        <span class="fechar" @click="modalAtivo = false">x</span>
        <h1>
          Você escolheu o número <u>{{ numeroEscolhido }}</u>
        </h1>
        <p>{{ textoAjuda }}</p>
        <h1>{{ textoAjudaComplemetar }}</h1>
      </div>
    </div>
    <header>
      <div id="header-imagem">
        <img src="./assets/images/gatinha.png" alt="gatinha" />
      </div>

      <div id="estrelas">
        <img src="./assets/images/estrela-1.png" alt="estrela" />
        <img src="./assets/images/estrela-2.png" alt="estrela" />
        <img src="./assets/images/estrela-3.png" alt="estrela" />
        <img src="./assets/images/estrela-2.png" alt="estrela" />
        <img src="./assets/images/estrela-3.png" alt="estrela" />
      </div>

      <div id="header-abertura">
        <h2>Chá Rifa da</h2>
        <h1>Ana Alice</h1>
      </div>

      <div id="header-premio">
        <h2><span>Prêmio</span></h2>
        <h1>R$ 100,00</h1>
      </div>

      <div id="header-exclicacao">
        <h2><span> Como funciona?</span></h2>
        <p>Cada número da rifa = <u>1 pacote de fraldas</u> ou <u>R$ 10,00</u></p>
        <p>Basta clicar no número desejado e enviar uma mensagem para a mamãe (Mikaely) avisando.</p>
        <h2>
          <a href="https://api.whatsapp.com/send?phone=+5575988108764&text=Oi,%20escolhi%20um%20numero%20da%20rifa." target="_blank" rel="noopener noreferrer"> (75) 98810-8764</a>
        </h2>
      </div>

      <div id="header-complemtos">
        <h2><span> Datas importantes</span></h2>
        <p>Limite para pagamento / entrega das fraldas: <u>03/10/2022</u></p>
        <p>Data do sorteio: <u>08/10/2022</u> às <u>19:00h</u></p>
        <p>O número vencedor será divulgado neste mesmo link</p>
      </div>

      <!-- Este bloque será desconsiderado no fluxo normal -->
      <img class="nuvem nuvem-1" src="./assets/images/numem-1.png" alt="nuvem1" />
      <img class="nuvem nuvem-2" src="./assets/images/numem-2.png" alt="nuvem2" />
      <img class="nuvem nuvem-3" src="./assets/images/numem-3.png" alt="nuvem3" />
      <img class="nuvem nuvem-4" src="./assets/images/numem-4.png" alt="nuvem4" />
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
        <div class="numero" :class="item.disponivel ? 'disponivel' : 'indisponivel'" v-for="(item, index) in listaBilhetes" :key="index" @click="ativarModal(item.numero, item.disponivel)">
          <span>
            {{ item.numero }}
          </span>
        </div>
      </section>
    </main>
  </div>
</template>

<script>
import data from '../public/data';

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
    ativarModal(numero, disponivel) {
      if (disponivel) {
        this.textoAjuda = 'Agora basta enviar uma mensagem para a mamãe (Mikaely) pedindo para reservarmos esse número.';
        this.textoAjudaComplemetar = '(75) 98810-8764.';
      } else {
        this.textoAjuda = 'Desculpe! Esse número já foi escolhido, tente outro.';
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
