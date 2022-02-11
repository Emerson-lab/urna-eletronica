<template>
  <div class="urna-teclado">
    <div class="urna-teclado-numerico">
      <div class="urna-teclado-numerico-linha">
        <button v-on:click="adcionarNumero(1)">1</button>
        <button v-on:click="adcionarNumero(2)">2</button>
        <button v-on:click="adcionarNumero(3)">3</button>
      </div>
      <div class="urna-teclado-numerico-linha">
        <button v-on:click="adcionarNumero(4)">4</button>
        <button v-on:click="adcionarNumero(5)">5</button>
        <button v-on:click="adcionarNumero(6)">6</button>
      </div>
      <div class="urna-teclado-numerico-linha">
        <button v-on:click="adcionarNumero(7)">7</button>
        <button v-on:click="adcionarNumero(8)">8</button>
        <button v-on:click="adcionarNumero(9)">9</button>
      </div>
      <div class="urna-teclado-numerico-linha">
        <button v-on:click="adcionarNumero(0)">0</button>
      </div>
    </div>
    <div class="urna-teclado-acoes">
      <button class="btn-branco">branco</button>
      <button class="btn-corrige" v-on:click="corrigir()">corrige</button>
      <button class="btn-confirma">confirma</button>
    </div>
  </div>
</template>

<script>
export default {
  name: "Teclado",
  props: {
    adcionarNumero: Function,
    corrigir: Function,
  },
};
</script>

<style scoped>
.urna-teclado {
  width: 40%;
  height: 100%;
  background-color: var(--ballot-box-keyboard-color);
  border-radius: 5px;
  padding: 20px;
  display: flex;
  flex-direction: column;
  justify-content: space-around;
}

.urna-teclado-numerico-linha {
  display: flex;
  justify-content: space-around;
  margin-bottom: 20px;
}

.urna-teclado-numerico-linha button:active {
  transform: translate3d(3px, 3px, 3px);
}

.urna-teclado-numerico {
  width: 100%;
}

.urna-teclado-numerico button {
  background-color: var(--ballot-box-keyboard-button-color);
  color: var(--light-text-color);
  font-size: 30px;
  border-radius: 5px;
  width: 80px;
  height: 50px;
}

.urna-teclado-acoes {
  display: flex;
  justify-content: space-around;
}

.urna-teclado-acoes button {
  color: var(--dark-text-color);
  font-size: 15px;
  border-radius: 5px;
  width: 30%;
  height: 50px;
  text-transform: uppercase;
}

.btn-branco:active,
.btn-corrige:active,
.btn-confirma:active {
  transform: translate3d(3px, 3px, 3px);
}

.btn-branco {
  background-color: var(--ballot-box-white-button-color);
}

.btn-corrige {
  background-color: var(--ballot-box-correct-button-color);
}
.btn-confirma {
  background-color: var(--ballot-box-confirm-button-color);
}
</style>
