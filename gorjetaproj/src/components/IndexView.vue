<script>
export default {
  data() {
    return {
      qualidades: [
        { qualidade: 5, servico: "5% (Péssimo)" },
        { qualidade: 10, servico: "10% (Ruim)" },
        { qualidade: 15, servico: "15% (OK)" },
        { qualidade: 20, servico: "20% (Bom)" },
        { qualidade: 25, servico: "25% (Mais que bom)" },
        { qualidade: 30, servico: "30% (Excelente)" },
      ],
      valor: 0,
      pessoa: 1,
      qualidade_selecionada: "",
    };
  },
  computed: {
    valor_final() {
      return (
        (this.valor * (1 + this.qualidade_selecionada / 100)) /
        this.pessoa
      ).toFixed(2);
    },
  },
};
</script>

<template>
  <div class="app">
    <div class="center">
      <h1>Calculadora de Gorjetas</h1>
      <form action="" class="formGorjeta">
        <label for="valorConta"> <p>Valor da conta:</p></label>
        <input name="valorConta" v-model="valor" type="number" />
        <label for="porcentagemServico"> <p>Como foi o serviço?</p> </label>
        <select v-model="qualidade_selecionada">
          <option value="" disabled selected>escolha aqui!</option>
          <option
            v-for="qualidade of qualidades"
            :key="qualidade.qualidade"
            for="select-servico"
            :value="qualidade.qualidade"
          >
            {{ qualidade.servico }}
          </option></select
        ><label for="qtdPessoas"> <p>Nº de pessoas pagando a conta:</p> </label
        ><input name="qtdPessoas" type="number" v-model="pessoa" />
      </form>

      <div class="resultado">
        <h3>Valor da conta:</h3>
        <span>R$ {{ valor_final }} por pessoa</span>
      </div>
    </div>
  </div>
</template>

<style>
#app {
  background-color: rgb(243, 217, 183);
  border-radius: 8px;
}
body {
  display: flex;
  place-items: center;
  align-items: center;
  justify-content: center;
}
h1 {
  font-size: 45px;
  font-family: "Verdana", ;
  text-align: center;
}

h3 {
  font-family: "Verdana", ;
}

form {
  padding: 8%;
  display: flex;
  flex-direction: column;
}

input,
select {
  padding: 1.5%;
  border-radius: 10px;
  margin: 10px;
}



p {
  font-family: "Verdana", ;
}
</style>
