<template>
  <div>
    <p>Component de Mensagem</p>
  </div>

  <form id="burguer-form">
    <div class="input-container">
      <label for="nome">Nome do cliente: </label>
      <input
        type="text"
        id="nome"
        name="nome"
        v-model="nome"
        placeholder="Digite seu nome"
      />
    </div>

    <div class="input-container">
      <label for="pao">Escolha o pao:</label>
      <select name="pao" id="pao" v-model="pao">
        <option value="">Selecione seu pão</option>
        <option v-for="pao in paes" :key="pao.id" value="pao.tipo">
          {{ pao.tipo }}
        </option>
      </select>
    </div>

    <div class="input-container">
      <label for="carne">
         Escolha a carne: 
        </label>
      <select name="carne" id="carne" v-model="carne">
        <option value="">Selecione sua carne</option>
        <option v-for="carne in carnes" :key="carne.id" value="carne.tipo">
          {{ carne.tipo }}
        </option>
      </select>
    </div>

    <div id="opcionais-container" class="input-container">
      <label id="opcionais-title" for="opcionais">Escolha os opcionais:</label>
      <div
        v-for="opcional in opcionaisData"
        :key="opcional.id"
        value="opcional.tipo"
        class="checkbox-container"
      >
        <input
          value="salame"
          name="opcionais"
          type="checkbox"
          v-model="opcionais"
        />
        <span>{{ opcional.tipo }}</span>
      </div>
    </div>
    <div id="input-container">
      <input type="submit" class="submit-btn" value="Crie meu Burguer!" />
    </div>
  </form>
</template>

<script>
export default {
  name: "BurguerForm",
  data() {
    return {
      paes: null,
      carnes: null,
      opcionaisData: null,
      pao: null,
      carne: null,
      opcionais: [],
      status: "solicitado",
      msg: null,
    };
  },
  methods: {
    async getIngredientes() {
      const req = await fetch("http://localhost:3000/ingredientes");
      const data = await req.json();

      this.paes = data.paes;
      this.carnes = data.carnes;
      this.opcionaisData = data.opcionais;
    },
  },
  mounted() {
    this.getIngredientes();
  },
};
</script>

<style scoped>
#burguer-form {
  max-width: 400px;
  margin: 0 auto;
}

.input-container {
  display: flex;
  flex-direction: column;
  margin-bottom: 20px;
}
label {
  font-weight: bold;
  margin-bottom: 15px;
  color: #222;
  padding: 5px 10px;
  border-left: 4px solid #fcba03;
}

input,
select {
  padding: 5px 10px;
  width: 300px;
}

#opcionais-container {
  flex-direction: row;
  flex-wrap: wrap;
}
#opcionais-title {
  width: 100%;
}
.checkbox-container {
  display: flex;
  align-items: flex-start;
  width: 50%;
  margin-bottom: 20px;
}
.checkbox-container span,
.checkbox-container input {
  width: auto;
}
.checkbox-container span {
  margin-left: 6px;
  color: #fcba03;
  font-weight: bold;
}
.submit-btn {
  background-color: #222;
  color: #fcba03;
  font-weight: bold;
  border: 2px solid #222;
  padding: 10px;
  font-size: 16px;
  margin: 0 auto;
  cursor: pointer;
  transition: 0.5s;
}
.submit-btn:hover {
  background-color: transparent;
  color: #222;
}
</style>
