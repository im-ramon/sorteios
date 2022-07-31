<template>
  <div id="container">
    <div class="animation-wrapper">
      <div class="particle particle-1"></div>
      <div class="particle particle-2"></div>
      <div class="particle particle-3"></div>
    </div>
    <div id="modal" v-if="modalAtivo" @click="fecharModal($event)">
      <div id="modal-area">
        <h1>TEXTO DE EXPLICAÇÃO</h1>
      </div>
    </div>
    <header>
      <div id="header-abertura">
        <h2>Texto aqui</h2>
        <h1>Texto aqui</h1>
      </div>

      <div id="header-premio">
        <h1>Texto cabeçalho</h1>
        <h1>Descrição cabeçalho</h1>
      </div>

      <div id="header-exclicacao">
        <span>Lorem ipsum dolor sit, amet consectetur adipisicing elit. Qui numquam voluptate, iste temporibus consequuntur repellendus obcaecati impedit praesentium tempora sunt nobis ipsum illo quisquam, voluptas earum animi aspernatur nulla natus. </span>
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
