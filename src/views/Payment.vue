<template>
    <div class="container">
        <Header/>
        <Back msg="Alterar forma de pagamento"/>
    </div>
</template>

<script>
import Header from '../components/Header'
import Back from '../components/Back'
export default {
  name: 'Payment',
  components: {
    Header,
    Back
  },
  props: {
    msg: String
  }
}
</script>

<style scoped>
.container{
}
</style>
