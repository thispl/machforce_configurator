<template>
  <div class="container">
    <!-- <div class="config-container"> -->
        <h1>Welcome</h1>
        <h2>Machforce Configurator Tool</h2>
      <table>
        <tr>
          <th>PIC Part Number</th>
          <th>connector side A</th>
          <th>Back Shell A</th>
          <th>Cable Type</th>
          <th>Cable length in Feet</th>
          <th>connector side B</th>
          <th>Back Shell A</th>
          <th>RJ45 part Number</th>
          <th>Price</th>
        </tr>
        <tr>
          <td>&nbsp;</td>
          <td></td>
          <td></td>
          <td></td>
          <td></td>
          <td></td>
          <td></td>
          <td></td>
          <td></td>
        </tr>
        <!-- <tr>
          <td></td>
          <td></td>
          <td></td>
          <td></td>
          <td></td>
          <td></td>
          <td></td>
          <td></td>
        </tr>
        <tr>
          <td></td>
          <td></td>
          <td></td>
          <td></td>
          <td></td>
          <td></td>
          <td></td>
          <td></td>
        </tr> -->
      </table>
    <!-- </div> -->
    <div><h4>Your Cart is Empty !</h4></div>
    <div class="actions">
      <button :class="{'show':showButton}">Start Purchase</button></div>
  </div>
  
</template>

<script>
// import Configurator from './components/Configurator.vue'
// import WelcomePage from './components/WelcomePage.vue'

export default {
  components: {
    // Configurator
    // WelcomePage
  },
};
</script>

<style lang="scss">
table {
  width: 100%;
  border-radius: 10px 0px 10px 10px;
  overflow: hidden;
  box-shadow: 0 15px 30px rgba(0, 0, 0, 0.2), 0 10px 10px rgba(0, 0, 0, 0.2);
}
tr:nth-child(odd) {
  background-color: deepskyblue;
}
th {
  padding: 10px;
  font-size:0.8rem;
  font-family: "Trebuchet MS", "Lucida Sans Unicode", "Lucida Grande",
    "Lucida Sans", Arial, sans-serif;
}
td {
  padding: 10px;
}

body {
  margin: 0;
  padding: 0;
}
h2 {
    font-size: 2rem;
    font-family: sans-serif;
    color: darkblue;
}
h1 {
    font-size: 3rem;
    color: skyblue;
}
.container {
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
  padding: 10px;
  margin-top: -50px;
  width: calc(100% - 20px);
  min-height: calc(100vh - 20px);
  font-family: "Ubuntu", Arial;
  font-size: 1rem;
  color: #333;
  background-size: cover;
  overflow: hidden;
}
.config-container {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(360px, 1fr));
  width: 100%;
  padding: 60px 20px;
  max-width: 720px;
  min-height: 480px;
  border-radius: 20px;
  overflow: hidden;
  box-shadow: 0 15px 30px rgba(0, 0, 0, 0.2), 0 10px 10px rgba(0, 0, 0, 0.2);
}
.actions {
    display: flex;
    justify-content: center;
    align-items:center;
    width: 100%;
    height: 20px;
  }

  button {
    outline: none;
    border: none;
    color: #fff;
    background-color:deepskyblue;
    font-family: 'Ubuntu', Arial;
    font-size: 1.2rem;
    padding: 5px 20px;
    border-radius: 5px;
    cursor: pointer;

    &.show {
      opacity: 1;
    }
  }
</style>