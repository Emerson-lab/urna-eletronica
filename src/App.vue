<template>
  <div id="app">
    <div class="urna">
      <Tela
        :tela="tela"
        :numeroVoto="numeroVoto"
        :quantidadeNumeros="quantidadeNumeros"
        :candidato="candidato"
      />
      <Teclado :adcionarNumero="adcionarNumero" :corrigir="corrigir" />
    </div>
  </div>
</template>

<script>
import "@/css/global.css";
import Teclado from "@/components/Teclado.vue";
import Tela from "@/components/Tela.vue";

export default {
  name: "App",
  methods: {
    adcionarNumero(numero) {
      //verifica limite de números votados
      if (this.numeroVoto.length == this.quantidadeNumeros) {
        return false;
      }
      //Adiciona o numero selecionado
      this.numeroVoto += "" + numero;

      //Verifica candidato votado
      this.verificarCandidato();
    },
    verificarCandidato() {
      //Voto incompleto
      if (this.numeroVoto.length < this.quantidadeNumeros) {
        return false;
      }

      //Verifica candidato existente
      if (this.candidatos[this.tela][this.numeroVoto]) {
        this.candidato = this.candidatos[this.tela][this.numeroVoto];
        return true;
      }

      //Voto nulo
      this.candidato = {
        nome: "Voto nulo",
        partido: "Voto nulo",
        imagem: "",
      };
    },
    corrigir() {
      this.limpar();
    },
    limpar() {
      this.candidato = {};
      this.numeroVoto = "";
    },
  },
  data() {
    return {
      tela: "prefeito",
      numeroVoto: "",
      quantidadeNumeros: 2,
      candidato: {},
      candidatos: {
        prefeito: {
          "01": {
            nome: "Ash",
            partido: "Pokemon",
            imagem:
              "https://raw.githubusercontent.com/william-costa/wdev-urna-eletronica-resources/master/images/ash.png",
          },
          "08": {
            nome: "Vegeta",
            partido: "Dragon Ball",
            imagem:
              "https://raw.githubusercontent.com/william-costa/wdev-urna-eletronica-resources/master/images/vegeta.png",
          },
        },
        vereador: {
          "01234": {
            nome: "Pikachu",
            partido: "Pokemon",
            imagem:
              "https://raw.githubusercontent.com/william-costa/wdev-urna-eletronica-resources/master/images/pikachu.png",
          },
          "08001": {
            nome: "Goku",
            partido: "Dragon Ball",
            imagem:
              "https://raw.githubusercontent.com/william-costa/wdev-urna-eletronica-resources/master/images/goku.png",
          },
        },
      },
    };
  },
  components: {
    Teclado,
    Tela,
  },
};
</script>

<style>
#app {
  background-color: var(--background-color);
  width: 100%;
  height: 100%;
  display: flex;
  justify-content: center;
  align-items: center;
}

.urna {
  width: 1000px;
  height: 500px;
  background-color: var(--ballot-box-background-color);
  padding: 30px;
  border-radius: 5px;
  display: flex;
  justify-content: space-between;
}
</style>
