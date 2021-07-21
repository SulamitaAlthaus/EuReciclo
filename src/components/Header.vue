<template>
  <div class="header">
    <div class="options">
      <div class="links"></div>
      <div class="links"></div>
      <div class="links"></div>
      <div class="links"></div>
      <div class="links"></div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Header",
};
</script>

<style scoped>
.header {
  width: 100%;
  height: 12vh;
  display: flex;
  align-items: center;
  justify-content: flex-end;
  border: 1 px solid black;
  box-shadow: 1px 1px 5px #c6c6c6;
  position: relative;
}
.options {
  display: flex;
  align-items: center;
  width: 45%;
  height: 65%;
  margin-right: 8%;
}
.links {
  width: 20%;
  height: 65%;
  background-color: #c6c6c6;
  margin: 10px;
  border-radius: 8px;
  cursor: pointer;
}
</style>
