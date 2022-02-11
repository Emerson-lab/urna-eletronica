<template>
  <div class="urna-tela">
    <div class="urna-tela-voto" v-if="tela !== 'fim'">
      <div class="urna-tela-voto-textos">
        <div class="urna-tela-voto-titulo">Seu voto para:</div>
        <div class="urna-tela-voto-tipo">{{ tela }}</div>
        <div class="urna-tela-voto-numeros">
          Números
          <div
            class="urna-tela-voto-numero"
            v-for="(value, key) in numeroVoto.padEnd(quantidadeNumeros, ' ')"
            :key="key"
          >
            {{ value }}
          </div>
        </div>
        <div class="urna-tela-voto-descricao">
          Nome: {{ candidato.nome ? candidato.nome : "________" }}
        </div>
        <div class="urna-tela-voto-descricao">
          Partido: {{ candidato.partido ? candidato.partido : "________" }}
        </div>
      </div>

      <div class="urna-tela-voto-imagens"></div>

      <div class="urna-tela-voto-instrucoes"></div>
    </div>
    <div class="urna-tela-fim" v-if="tela === 'fim'">finalização</div>
  </div>
</template>

<script>
export default {
  name: "Tela",
  props: {
    tela: String,
    numeroVoto: String,
    quantidadeNumeros: Number,
    candidato: Object,
  },
};
</script>

<style scoped>
.urna-tela {
  width: 55%;
  height: 100%;
  background-color: var(--ballot-box-screen-color);
  border-radius: 5px;
  border: 1px solid var(--light-border-color);
  padding: 20px;
  color: var(--dark-text-color);
}

.urna-tela-voto-titulo {
  font-size: 20px;
}

.urna-tela-voto-tipo {
  font-size: 30px;
  font-weight: bold;
  margin: 20px 0;
  text-transform: uppercase;
}

.urna-tela-voto-numeros {
  display: flex;
  align-items: center;
}

.urna-tela-voto-numero {
  width: 45px;
  height: 55px;
  border: 1px solid var(--dark-border-color);
  margin-left: 10px;
  display: flex;
  justify-content: center;
  align-items: center;
  font-size: 30px;
}
</style>
