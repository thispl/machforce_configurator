<template>
  <div class="container">
    <div class="config-container">
      <div id="app">
        <table v-if="tableData" :theData="tableData"></table>
      </div>
      </div></div>
</template>

<script>
// import Table from './components/Table'
export default {
  // components:{
  //   Table
  // },
  data:()=>({
    tableData : {}
  })
}
</script>

<style lang="scss" scoped>
@import url("https://fonts.googleapis.com/css?family=Ubuntu&display=swap");

.container {
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;

  padding: 10px;
  width: calc(100% - 20px);
  min-height: calc(100vh - 20px);
  font-family: "Ubuntu", Arial;
  font-size: 1rem;
  color: #333;

  // background: url(../assets/app_breakfast.jpg) center center;
  background-size: cover;
  overflow: hidden;
}
.config-container {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(360px, 1fr));
  width: 100%;
  max-width: 720px;
  min-height: 480px;
  border-radius: 20px;
  overflow: hidden;
  box-shadow: 0 15px 30px rgba(0, 0, 0, 0.2), 0 10px 10px rgba(0, 0, 0, 0.2);
}
</style>