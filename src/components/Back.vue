<template>
  <div class="container">
    <div class="back">
      <img src="../assets/img/arrowLeft.svg" alt="" />
      <h1>{{ msg }}</h1>
    </div>
  </div>
</template>

<script>
export default {
  name: "Back",
  props: {
    msg: String,
  },
};
</script>

<style scoped>
.container {
  width: 30%;
  height: 88vh;
  background-color: #01ee55;
  display: flex;
  justify-content: flex-end;
}
.back {
  width: 70%;
  height: 10%;
  display: flex;
  justify-content: space-between;
  margin: 15% 5% 0 0;
  align-items: center;
  cursor: pointer;
}
.back img {
  width: 6%;
  margin-left: 15px;
}
.back h1 {
  color: #ffffff;
  font-size: 18px;
  font-family: "Segoe UI", sans-serif;
  font-weight: 400;
}
@media screen and (max-width: 768px) {
  .container {
    width: 100%;
    height: 30vh;
    justify-content: center;
  }
  .back {
    width: 50%;
    justify-content: center;
    margin: 15%;
  }
}
</style>
