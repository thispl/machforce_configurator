<template>
  <div class="container">
    <ConfiguratorProgress :activeConfigStep="activConfigStep" :configuration="configuration" />
    <div class='closebtn'>
          <button id="close" v-on:click="closecfg">X</button>
    </div>
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
        <div v-if="configuration[activConfigStep].display=='filter'" > <vue-bootstrap-typeahead 
            :data="currentOptions"
            @hit="filter=$event; applyfilter()"
             /> 
        </div>
        <div v-if="configuration[activConfigStep].display=='text'" >
          <b-form-input v-model="textValue"
          v-on:keyup="calcPrice"  v-on:blur="moveStep"
           placeholder="Enter Value" ></b-form-input>
            
        </div>
        <ConfiguratorOptions
          v-if="activConfigStep + 1 < configuration.length"
          :activeConfigStep="activConfigStep"
          :configuration="configuration"
          :filter="filter"
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
import VueBootstrapTypeahead from 'vue-bootstrap-typeahead'

export default {
  data: () => {
    return {
      activConfigStep: 0,
      filter:"", 
      textValue:"",
      showButton:true,
     // selectedValue:"",
      currentOptions:[], 
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
          display:'filter'
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
          display:'filter'
        },
        {
          title: "MachForce Back Shell A",
          selectedOption: {},
          options: [
            { title: "MF3825S", img: "", price: 0.49 },
            { title: "MF3825US", img: "", price: 0.49 },
          ],
          display:'filter'
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
          display:'filter'
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
          display:'text'
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
          display:'filter'
        },
        {
          title: "MachForce Back Shell A",
          selectedOption: {},
          options: [
            { title: "MF3825S", img: "", price: 0.49 },
            { title: "MF3825US", img: "", price: 0.49 },
          ],
          display:'filter'
        },
        {
          title: "RJ45 part Number",
          selectedOption: {},
          options: [
            { title: "110630", img: "", price: 0.49 },
          ],
          display:'filter'
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
    VueBootstrapTypeahead
  },
  methods: {
    applyfilter() {
    //  console.log(this.filter);
    },
    moveStep(){
      this.activConfigStep += 1;
      this.getOptions(this.configuration[this.activConfigStep]); 
    } 
    , 
    calcPrice(){
     // console.log("Running Calc " + this.textValue )
      
       var allOptions = this.configuration[this.activConfigStep].options
       for(let element of allOptions) {
          if (parseInt(element.title) >= this.textValue) 
          {
            //console.log('element.title ' + element.title + ' val ' + this.textValue )
            let option = Object.assign({}, element);

           // console.log(this.textValue * option.price);
            option.title = this.configuration[this.activConfigStep].title.split(' ')[0] + ' ' + this.textValue +' x ' + element.price;
            option.price = (this.textValue * element.price).toFixed(2);
            this.configuration[this.activConfigStep].selectedOption = option; 
           // this.configuration[this.activConfigStep].selectedOption.price = this.textValue * element.price; 
            break;
          }
       }
       this.calcTotalPrice(); 
    }, 
    getOptions(config) {
        var titles = [];
        if (config.options){
          config.options.forEach(element => {
           titles.push(element.title);
          });
        }
  
       // console.log(titles)
        this.currentOptions = titles; 
        return titles;
    }, 
    closecfg(){
      this.$emit('closeConfig');
    }, 
    calcTotalPrice(){
     let totalPrice = 0;
     this.configuration.forEach((element) => {
            var elemPrice = 0.0 
            if(element.selectedOption.price){
              elemPrice = parseFloat(element.selectedOption.price)
              totalPrice += elemPrice;
             // console.log(totalPrice)
              this.configuration[8].selectedOption.price = totalPrice.toFixed(2);
            }
        });
    }, 
    selectOption(option) {
      
      this.configuration[this.activConfigStep].selectedOption = option;
      this.activConfigStep += 1;

      this.calcTotalPrice()
      this.getOptions(this.configuration[this.activConfigStep]); 
      this.filter=""; 
      // }
    },
  },
    created: function () {
    // `this` points to the vm instance
     this.getOptions(this.configuration[0]); 
  }
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
  grid-template-columns: repeat(2, minmax(360px, 1fr));
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
.closebtn{
  width: 800px;
  height: 5%;
  padding: 10px;
  text-align:right; 
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
