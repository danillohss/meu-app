<template>
  <div id="App">
    <h1>Fazer Cadastro</h1>
    <div>
      <form>
        <label>Nome</label>
        <input type="text" v-model="user.nome" /><br />
        <label>Email</label>
        <input type="email" v-model="user.email" /><br />
        <label>Quantidade de Funcionários</label>
        <input type="number" v-model="user.qtdFunc" /><br />
        <label>Opiniao</label>
        <textarea v-model="opiniao"></textarea>
        <label>Tecnologias</label>
        <span>
          <input type="checkbox" value="javascript" v-model="tecno" />JavaScript
        </span>
        <span> <input type="checkbox" value="css" v-model="tecno" />CSS </span>
        <span>
          <input type="checkbox" value="vuejs" v-model="tecno" />VueJS
        </span>
        <label>Qual tipo de contratação?</label>
        <select v-model="tipoSelecionado">
          <option v-for="item in tipos" :key="item.id" :value="item.nome">
            {{ item.nome }}
          </option></select
        ><br />
        <label>Senioridade:</label>
        <span><input type="radio" value="basico" v-model="nivel" />Básico</span>
        <span
          ><input
            type="radio"
            value="intermediario"
            v-model="nivel"
          />Intermediário</span
        >
        <span
          ><input type="radio" value="avancado" v-model="nivel" />Avançado</span
        >
      </form>
      <br />
      <button @click.prevent="submit">Enviar Formulário</button>
    </div>
    <hr />
    <div class="item" v-show="resultado">
      <h2>Usuario Cadastrado</h2>
      <label>Nome: {{ user.nome }}</label
      ><br />
      <label>Email: {{ user.email }}</label
      ><br />
      <label>Quantidade de Funcionários: {{ user.qtdFunc }}</label
      ><br />
      <label>Sua opinião: {{ opiniao }}</label
      ><br />
      <label>Tecnologias:</label><br />
      <ul>
        <li v-for="tec in tecno" v-bind:key="tec">{{ tec }}</li>
      </ul>
      <label>Tipo de contratação: {{ tipoSelecionado }}</label
      ><br />
      <label>Nivel: {{ level }}</label>
    </div>
  </div>
</template>
<script>
export default {
  name: "App",
  data() {
    return {
      user: {
        nome: "",
        email: "",
        qtdFunc: 0,
      },
      opiniao: "",
      tecno: [],
      tipos: [
        { id: 1, nome: "FreeLancer" },
        { id: 2, nome: "CLT" },
        { id: 3, nome: "PJ" },
        { id: 4, nome: "Remoto" },
      ],
      tipoSelecionado: null,
      nivel: null,
      level: null,
      resultado: false,
    };
  },
  methods: {
    submit() {
      this.resultado = true;
    },
  },
  watch: {
    nivel() {
      if (this.nivel === "basico") {
        this.level = "Básico";
      } else if (this.nivel === "intermediario") {
        this.level = "Intermediário";
      } else {
        this.level = "Avançado";
      }
    },
  },
};
</script>

<style scoped>
form {
  display: flex;
  flex-direction: column;
}
</style>