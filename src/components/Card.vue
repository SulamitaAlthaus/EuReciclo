<template>
    <div class="container">
        <img src="../assets/img/mastercard.png" alt="">
        <div class="content">
            <h1 class="numberCard">{{numberCard}}</h1>
            <h1 class="name">{{name}}</h1>
            <div class="footer">
                <label>VALIDADE
                <h1 class="validity">{{validity}}</h1></label>
                <label>CVV
                <h1 class="cvv">{{cvv}}</h1></label>
            </div>
        </div>
    </div>
</template>

<script>
export default {
  name: 'Card',
  props: {
    numberCard: Number,
    name: String,
    validity: String,
    cvv: Number
  }
}
</script>

<style scoped>
@font-face {
    font-family: kredit;
    src: url(../assets/font/kredit-front.ttf);
}
.container{
    display: grid;
    width: 30vw;
    height: 38vh;
    background: radial-gradient(#707070, #363636);
    border-radius: 10px;
    box-shadow: 1px 5px 10px #C6C6C6;
    padding: 0 15px;
    align-items: center;
}
.container img{
    position: absolute;
    right: 0;
    margin: 10px 10px 0 0 ;

}
.content{
    display: block;
    color: #C6C6C6;
    font-family: kredit;
    font-size: 16px;
    text-align: left;
    line-height: 20px;
    padding: 0 15px;
}
.name{
    font-size: 20px;
    font-weight: normal;
}
.footer{
    display: flex;
    justify-items: left;
    justify-content: space-between;
    width: 50%;
    line-height: 15px;
    font-size: 15px;
}
.footer label{
    font-weight: 800;
}
.footer h1{
    font-size: 15px;
    font-weight: normal;
}
</style>
