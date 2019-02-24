<template>
  <div class="hello">
    <h1> Coffee Calculator </h1>
    <h2> Brew Method </h2>
      <select v-model="brew_method"> <!--binds brew_method to data in javascript-->
        <option value="volvo">French Press</option>
        <option value="saab">Aeropress</option>
        <option value="mercedes">Drip</option>
        <option value="audi">Pour Over</option>
      </select>
    <br>
    Ground coffee (grams): <input type="text" v-model="ground_coffee" ><br>
    Water (grams): <input type="text" v-model="water" ><br>
    <h3>selected brew method: {{ brew_method }}</h3> 

  </div>
</template>

<script>
export default {
  name: 'CoffeeCalculator',
  props: {},
  data() {
    return {
    brew_method: 'audi',
    ground_coffee: '0',
    water: '0'
    }
  },
  watch: {
    ground_coffee(val,old_val) {
      console.log('calculate event',val,old_val)
      this.$set(this, 'water', val*16)
    },
      water(val,old_val) {
      console.log('calculate event',val,old_val)
      this.$set(this, 'ground_coffee', val*(1/16))
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
