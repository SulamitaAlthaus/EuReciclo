<template>
  <div class="container">
    <Header class="header" />
    <div class="backMobile">
      <Back msg="Etapa 2 de 3" />
    </div>
    <div class="card">
      <Card
        :numberCard="numberCard ? numberCard : '5555 5555 5555 5555'"
        :name="name ? name : 'Walter J. White'"
        :validity="validity ? validity : '12/26'"
        :cvv="cvv ? cvv : '123'"
      />
    </div>

    <div class="content">
      <div class="path">
        <div class="pathDiv">
          <img src="../assets/img/check.svg" class="circle" />
          <h1>Carrinho</h1>
          <img src="../assets/img/arrow.svg" class="arrow" />
        </div>
        <div class="pathDiv">
          <img src="../assets/img/circle-two.svg" class="circle" />
          <h1>Pagamento</h1>
          <img src="../assets/img/arrow.svg" class="arrow" />
        </div>
        <div class="pathDiv">
          <img src="../assets/img/circle-three.svg" class="circle" />
          <h1>Pedido Finalizado</h1>
        </div>
      </div>
      <label>Número do cartão</label>
      <input
        id="numberCard"
        v-model="numberCard"
        v-mask="'#### #### #### ####'"
        :style="{
          borderBottom: validation && !numberCard ? '1px solid #FF0000' : null,
        }"
      />
      <span v-if="validationNumberCard || (validation && !numberCard)"
        >Número do cartão inválido</span
      >

      <label>Nome</label>
      <input
        id="name"
        v-model="name"
        :style="{
          borderBottom: validation && !name ? '1px solid #FF0000' : null,
        }"
      />
      <span v-if="validation && !name">Insira seu nome completo</span>

      <div class="cardInformation">
        <label
          >Validade (MM/AA)
          <input
            id="validity"
            v-model="validity"
            v-mask="'##/##'"
            :style="{
              borderBottom:
                validation && !validity ? '1px solid #FF0000' : null,
            }"
          />
          <span v-if="validation && !validity">Data Inválida</span>
        </label>

        <label
          >CVV
          <img
            src="../assets/img/information.svg"
            title="O código de segurança do cartão"
          />
          <input
            id="cvv"
            v-model="cvv"
            v-mask="'###'"
            :style="{
              borderBottom: validation && !cvv ? '1px solid #FF0000' : null,
            }"
          />
          <span v-if="validation && !cvv">CVV não informado</span>
        </label>
        <label class="cpf"
          >CPF
          <input
            id="cpf"
            v-model="cpf"
            v-mask="'###.###.###-##'"
            :style="{
              borderBottom: validation && !cpf ? '1px solid #FF0000' : null,
            }"
          />
          <span v-if="validation && !cpf">CPF inválido</span>
        </label>
      </div>

      <div class="cpfMobile">
        <label>CPF </label>
        <input
          id="cpf"
          v-model="cpf"
          v-mask="'###.###.###-##'"
          :style="{
            borderBottom: validation && !cpf ? '1px solid #FF0000' : null,
          }"
        />
        <span v-if="validation && !cpf">CPF inválido</span>
      </div>

      <label>Número de parcelas</label>
      <select
        id="installment"
        v-model="installment"
        :style="{
          borderBottom: validation && !installment ? '1px solid #FF0000' : null,
        }"
      >
        <option :value="1">1x R$1.198,80 (à vista)</option>
        <option :value="2">2x R$599,40</option>
        <option :value="3">3x R$399,60</option>
        <option :value="4">4x R$299,70</option>
        <option :value="5">5x R$239,76</option>
      </select>
      <span v-if="validation && !installment"
        >Escolha o número de parcelas</span
      >

      <button @click="setPayment">Pagar</button>
    </div>
    <div class="back">
      <Back msg="Alterar forma de pagamento" />
    </div>
    <div v-if="loading" class="loading">
      <img src="../assets/img/loading.gif" />
    </div>
  </div>
</template>

<script>
import Header from "../components/Header";
import Card from "../components/Card";
import Back from "../components/Back";

export default {
  name: "Payment",
  components: {
    Header,
    Card,
    Back,
  },
  data: () => ({
    numberCard: "",
    name: "",
    validity: "",
    cvv: "",
    cpf: "",
    installment: "",
    validation: false,
    validationNumberCard: false,
    loading: false,
  }),
  methods: {
    async setPayment() {
      this.validation = true;
      if (this.numberCard.split(" ").join("").length < 16) {
        this.validationNumberCard = true;
        return;
      }
      if (
        !this.numberCard ||
        !this.name ||
        !this.validity ||
        !this.cvv ||
        !this.cpf ||
        !this.installment
      ) {
        return;
      } else {
        this.validationNumberCard = false;
        this.loading = true;

        //   await api
        //     .post(`/newsolicitation`, {
        //       numberCard: this.numberCard,
        //       name: this.name,
        //       validity: this.validity,
        //       cvv: this.cvv,
        //       cpf: this.cpf,
        //       installment: this.installment,
        //     })
        //     .then(() => {
        //       setRedirect(true);
        //     })
        //     .catch((err) => {
        //       console.log(err);
        //     });
      }
    },
  },
};
</script>

<style scoped>
.container {
  overflow: hidden;
}
.backMobile {
  display: none;
}
.card {
  position: absolute;
  margin: 15% 8%;
}
.path {
  width: 100%;
  display: flex;
}
.pathDiv {
  display: flex;
  width: 35%;
  align-items: center;
  justify-content: left;
}
.pathDiv h1 {
  font-size: 18px;
  color: #01ee55;
  font-family: "Segoe UI", sans-serif;
  font-weight: 500;
}
.pathDiv img {
  width: 15%;
  margin: 2%;
}
.arrow {
  height: 30px;
  padding-left: 15%;
}
.content {
  display: flex;
  flex-direction: column;
  float: right;
  width: 50%;
  margin-right: 20px;
  line-height: 40px;
}
.content label {
  text-align: left;
  color: #c6c6c6;
  font-family: "Segoe UI", sans-serif;
}
.content input,
select {
  height: 30px;
  border: none;
  border-bottom: 1px solid #c6c6c6;
  outline: none;
  color: #707070;
}
.cardInformation {
  display: flex;
  width: 100%;
  justify-content: space-between;
}
.cardInformation label {
  width: 25%;
  margin-bottom: 10px;
}
.cardInformation input {
  width: 100%;
  color: #707070;
}
span {
  color: #ff0000;
  font-size: 12px;
  text-align: left;
  line-height: 15px;
}
.cardInformation label span {
  position: absolute;
}
img {
  width: 8%;
  cursor: pointer;
}
.cpfMobile {
  display: none;
}
button {
  background-color: #01ee55;
  border: none;
  cursor: pointer;
  color: #ffffff;
  font-size: 18px;
  width: 150px;
  height: 60px;
  border-radius: 10px;
  margin: 5% 0 5% auto;
}
button:hover {
  box-shadow: 1px 5px 10px #c6c6c6;
}
.loading {
  display: flex;
  width: 100%;
  height: 100vh;
  background: rgba(207, 207, 207, 0.5);
  position: absolute;
  justify-content: center;
  align-items: center;
  margin: auto;
  top: 0;
}
@media screen and (max-width: 1024px) {
  .pathDiv h1 {
    font-size: 15px;
  }
}
@media screen and (max-width: 768px) {
  .header {
    display: none;
  }
  .path {
    display: none;
  }
  .pathDiv h1 {
    font-size: 15px;
  }
  .back {
    display: none;
  }
  .backMobile {
    display: block;
  }
  .card {
    top: 10%;
    margin: 15%;
  }
  .content {
    float: none;
    width: 80%;
    margin: 25% auto 0 auto;
    font-size: 15px;
  }
  img {
    width: 10%;
  }
  .cpf {
    display: none;
  }
  .cpfMobile {
    display: grid;
  }
  .cardInformation label {
    width: 45%;
  }
  .cardInformation span {
    display: flex;
  }

  button {
    width: 100%;
    margin: 5% auto;
  }
}
</style>
