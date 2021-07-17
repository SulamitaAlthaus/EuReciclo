<template>
    <div class="container">
        <Header/>
        <div class="card">
          <Card :numberCard="numberCard ? numberCard : '5555 5555 5555 5555'" 
          :name="name ? name : 'Walter J. White'" 
          :validity="validity ? validity : '12/26'" 
          :cvv="cvv ? cvv : '123'" />
        </div>
        <div class="content">
          <label for="">Número do cartão</label>
          <input type="text" 
          v-model="numberCard" 
          v-mask="'#### #### #### ####'">

          <label for="">Nome</label>
          <input type="text" v-model="name">

          <div class="cardInformation">
            <label>Validade (MM/AA)
              <input type="text" 
              v-model="validity"
              v-mask="'##/##'">
            </label>

            <label>CVV
              <input type="text" 
              v-model="cvv"
              v-mask="'###'">
            </label>

            <label>CPF
              <input type="text" 
              v-model="cpf"
              v-mask="'###.###.###-##'">
            </label>
          </div>

          <label for="">Número de parcelas</label>
          <input type="text" v-model="installment">
        </div>
        <Back msg="Alterar forma de pagamento"/>
    </div>
</template>

<script>
import Header from '../components/Header'
import Card from '../components/Card'
import Back from '../components/Back'
export default {
  name: 'Payment',
  components: {
    Header,
    Card,
    Back
  },
  data(){
    return {
      numberCard: "",
      name: "",
      validity: "",
      cvv: "",
      cpf: "",
      installment: ""
    }
  }
}
</script>

<style scoped>
.container{
  overflow: hidden;
}
.card{
  position: absolute;
  margin: 15% 8%;
}
.content{
  display: flex;
  flex-direction: column;
  float: right;
  width: 50%;
  margin-right: 20px;
  line-height: 40px;
}
.content label{
  text-align: left;
  color: #C6C6C6;
  font-family: 'Segoe UI', sans-serif;
}
.content input{
  height: 30px;
  border: none;
  border-bottom: 1px solid #C6C6C6;
  outline: none;
}
.cardInformation{
  display: flex;
  width: 100%;
  justify-content: space-between;
}
.cardInformation label{
  width: 25%;
}
.cardInformation input{
  width: 100%;
}
</style>
