<template>
  <div id="container">
    <div id="modal" v-if="modalAtivo" @click="fecharModal($event)">
      <div id="modal-area">
        <h1>TEXTO DE EXPLICAÇÃO</h1>
        <p>Colocar aqui o passo a passo para registrar o número.</p>
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
        <h1>R$ 200,00</h1>
      </div>

      <div id="header-exclicacao">
        <h2><span> Como funciona?</span></h2>
        <p>Cada número da rifa = 1 pacote de fraldas ou R$ 20,00</p>
        <p>Basta escolher um número, e enviar mensagem para a mamãe (Mikaely) para avisar.</p>
        <h2>
          <a href="https://api.whatsapp.com/send?phone=+5575988108794&text=Ol%C3%A1,%20peguei%20seu%20n%C3%BAmero%20no%20site." target="_blank" rel="noopener noreferrer"> (75) 98810-8764</a>
        </h2>
      </div>

      <div id="header-complemtos">
        <h2><span> Data importantes</span></h2>
        <p>Limite para pagamento / entrega da fralda: 00/00/0000</p>
        <p>Data do sorteio: 00/00/0000</p>
      </div>

      <!-- Este bloque será desconsiderado no fluxo normal -->
      <img class="nuvem nuvem-1" src="./assets/images/numem-1.png" alt="nuvem1" />
      <img class="nuvem nuvem-2" src="./assets/images/numem-2.png" alt="nuvem2" />
      <img class="nuvem nuvem-3" src="./assets/images/numem-3.png" alt="nuvem3" />
      <img class="nuvem nuvem-4" src="./assets/images/numem-4.png" alt="nuvem4" />
    </header>

    <main>
      <section id="numeros">
        <div class="numero" :class="item.disponivel ? 'disponivel' : 'indisponivel'" v-for="(item, index) in listaBilhetes" :key="index">
          <span @click="modalAtivo = true">
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
    };
  },
  methods: {
    fecharModal(e) {
      if (e.target.id === 'modal') {
        this.modalAtivo = false;
      }
    },
  },
};
</script>
