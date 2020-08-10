<template>
  <div class="container">
    <ConfiguratorProgress :activeConfigStep="activConfigStep" :configuration="configuration" />
    <div class="config-container">
      <div class="order-info">
        <div>
          <h2>Machforce Configurator Tool</h2>
          <ConfiguratorOrder
        :configuration="configuration" />
        </div>
      </div>

      <div class="selection">
        <h3>{{ configuration[activConfigStep].title }}</h3>
        <ConfiguratorOptions
          v-if="activConfigStep + 1 < configuration.length"
          :activeConfigStep="activConfigStep"
          :configuration="configuration"
          @chooseOption="selectOption" />
        <!-- <ConfiguratorOrder
          v-else
        :configuration="configuration" /> -->
      
        <div v-if="activConfigStep + 1 == configuration.length" class="actions">
      <button :class="{'show':showButton}">Continue Purchase</button>
        </div>
        <div v-if="activConfigStep + 1 == configuration.length" class="actions">
      <button :class="{'show':showButton}">Order Now</button>
    </div>
      </div>
    </div>
  </div>
</template>

<script>
import ConfiguratorProgress from "./ConfiguratorProgress.vue";
import ConfiguratorOptions from "./ConfiguratorOptions.vue";
import ConfiguratorOrder from "./ConfiguratorOrder.vue";

export default {
  data: () => {
    return {
      activConfigStep: 0,
      configuration: [
        {
          title: "PIC Part Number",
          selectedOption: {},
          options: [
            { title: "11012-XXXX-01", img: ""},
            { title: "11012-XXXX-02", img: ""},
            { title: "11012-XXXX-03", img: ""},
            { title: "11012-XXXX-04", img: ""},
          ],
        },
        {
          title: "MachForce connector side A",
          selectedOption: {},
          options: [
            { title: "MF3825PPWA(Plug A Key)", img: "", price: 0.99 },
            { title: "MF3825PPWB(Plug B Key)", img: "", price: 1.49 },
            { title: "MF3825PPWC(Plug C Key)", img: "", price: 1.49 },
            { title: "MF3825PPWD(Plug D Key)", img: "", price: 1.29 },
            { title: "MF3825PPWN(Plug N Key)", img: "", price: 1.99 },
            { title: "MF3825FSWA(Flange A Key)", img: "", price: 1.99 },
            { title: "MF3825FSWB(Flange B Key)", img: "", price: 0.99 },
            { title: "MF3825FSWC(Flange C Key)", img: "", price: 1.79 },
            { title: "MF3825FSWD(Flange D Key)", img: "", price: 1.79 },
            { title: "MF3825FSWN(Flange N Key)", img: "", price: 1.79 },
          ],
        },
        {
          title: "MachForce Back Shell A",
          selectedOption: {},
          options: [
            { title: "MF3825S", img: "", price: 0.49 },
            { title: "MF3825US", img: "", price: 0.49 },
          ],
        },
        {
          title: "Cable Type",
          selectedOption: {},
          options: [
            { title: "E6A6824", img: ""},
            { title: "E686826", img: ""},
            { title: "E74824", img: ""},
            { title: "E74826", img: ""},
          ],
        },
        {
          title: "Cable length in Feet",
          selectedOption: {},
          options: [
            { title: "25", img: "", price: 2 },
            { title: "50", img: "", price: 1.8 },
            { title: "100", img: "", price: 1.5 },
            { title: "250", img: "", price: 1.3 },
            { title: "500", img: "", price: 1.1 },
            { title: "1000", img: "", price: 1 },
            { title: "2500", img: "", price: 0.9 },
            { title: "5000", img: "", price: 0.89 },
            { title: "15000", img: "", price: 0.88 },
          ],
        },
        {
          title: "MachForce connector side B",
          selectedOption: {},
          options: [
            { title: "MF3825PPWA(Plug A Key)", img: "", price: 0.99 },
            { title: "MF3825PPWB(Plug B Key)", img: "", price: 1.49 },
            { title: "MF3825PPWC(Plug C Key)", img: "", price: 1.49 },
            { title: "MF3825PPWD(Plug D Key)", img: "", price: 1.29 },
            { title: "MF3825PPWN(Plug N Key)", img: "", price: 1.99 },
            { title: "MF3825FSWA(Flange A Key)", img: "", price: 1.99 },
            { title: "MF3825FSWB(Flange B Key)", img: "", price: 0.99 },
            { title: "MF3825FSWC(Flange C Key)", img: "", price: 1.79 },
            { title: "MF3825FSWD(Flange D Key)", img: "", price: 1.79 },
            { title: "MF3825FSWN(Flange N Key)", img: "", price: 1.79 },
          ],
        },
        {
          title: "MachForce Back Shell A",
          selectedOption: {},
          options: [
            { title: "MF3825S", img: "", price: 0.49 },
            { title: "MF3825US", img: "", price: 0.49 },
          ],
        },
        {
          title: "RJ45 part Number",
          selectedOption: {},
          options: [
            { title: "110630", img: "", price: 0.49 },
          ],
        },
        {
          title: "Thank You!",
          selectedOption: { title: "Total", price: 0 },
        },
      ],
    };
  },
  components: {
    ConfiguratorProgress,
    ConfiguratorOptions,
    ConfiguratorOrder,
  },
  methods: {
    selectOption(option) {
      this.configuration[this.activConfigStep].selectedOption = option;
      this.activConfigStep += 1;

      // if (this.activConfigStep + 1 === this.configuration.length) {
        let totalPrice = 0;
        this.configuration.forEach((element) => {
            if(element.selectedOption.price){
          totalPrice += element.selectedOption.price;
          console.log(totalPrice)
          this.configuration[8].selectedOption.price = totalPrice.toFixed(2);
            }
        });
      // console.log(this.configuration)
        
      // }
    },
  },
};
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

.selection {
  min-height: 480px;
  background-color: rgba($color: White, $alpha: 0.8);
  overflow: hidden;

  h3 {
    text-align: center;
  }
}

.order-info {
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
  min-height: 480px;
  padding: 10px;
  color:darkblue;
  text-align: center;
  background-color: rgba($color:deepskyblue, $alpha: 0.8);

  @media only screen and (max-width: 740px) {
    min-height: fit-content;
  }
}
.actions {
    display: flex;
    justify-content: center;
    align-items: center;
    width: 100%;
    height: 140px;
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
    // opacity: 0;
    // transition: opacity .5s ease-in-out;

    &.show {
      opacity: 1;
    }
  }
</style>
