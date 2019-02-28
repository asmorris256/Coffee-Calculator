<template>
  <div class="coffee-calculator">
    <h1> Coffee Calculator </h1>
    <h2> Brew Method </h2>
    <div class="row">
    <div class="col-xs-12 col-sm-8 offset-sm-2 col-md-8 offset-md-2 col-lg-6 offset-lg-3"> <!--media query via bootstrap-->

      <b-form-select v-model="brew_method" id="brew-method"> <!--binds brew_method to data in javascript-->
        <option :value="null">Select your brewing method</option>   <!--initializes drop down menu-->
        <option value="fp">French Press</option>
        <option value="ap">Aeropress</option>
        <option value="dr">Drip</option>
        <option value="po">Pour Over</option>
      </b-form-select>
    <br>
    <b-form-group label="Ground coffee (grams)" label-for="ground-coffee">
    <b-form-input id="ground-coffee" type="number" step="0.01" v-model="ground_coffee" />
    </b-form-group>
    Water (grams): <b-form-input type="number" step="0.01" v-model="water" /><br>
          
    </div>
    </div>

  </div>
</template>

<script>

const format_number = (number) => {
  return parseFloat(number).toFixed(1);
} 
export default {
  name: 'CoffeeCalculator',
  props: {},
  data() {
    return {
    brew_method: null,
    ground_coffee: 0.00,
    water: 0.00
    }
  },
  watch: {            //performs basic calculation automatically when value is changed by user
    ground_coffee(val) {
      console.log('calculate event',val)
      const water = this.calculate(this.brew_method,val,null)
      this.$set(this, 'water', water)
    },
    water(val) {
      console.log('calculate event',val)
      const coffee = this.calculate(this.brew_method,null,val)
      this.$set(this, 'ground_coffee',coffee)
    },

    brew_method(val){     //
      this.$set(this, 'ground_coffee',this.calculate(this.brew_method,null,this.water))  //if user changes brew method after value is entered
    }
  },
  methods: {
    calculate (brew_method,amnt_grounds,amnt_water) {
      const ratios = { //all ratios coffee:water
        fp: 1/17,
        ap: 1/13,
        dr: 1/15,
        po: 1/16
      }
      if (amnt_grounds === null) {
        return amnt_water*ratios[brew_method]
      } else {
        return amnt_grounds/ratios[brew_method]
      }

    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

.coffee-calculator {
  background-color: rgb(29, 214, 190);
  padding: 20px 0 20px 0;
}

#brew-method {
  background-color: aquamarine;
}

.input_width {
  width: 60%;
  margin: auto;
}
</style>
