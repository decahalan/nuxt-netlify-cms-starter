<template>
  <div class="container">
    <div>
      <h1>{{ teaName }}</h1>
    </div>
    <div>
      <form
        name="vue-tea"
        method="post"
        data-netlify="true"
        data-netlify-honeypot="bot-field"
      >
        <input type="hidden" name="form-name" value="vue-tea" />
        <input id="name" name="name" type="string" />
        <div class="tea">
          <h2>Pick a Tea</h2>
          <label
            v-for="tea in teaNames"
            :key="tea"
            :class="{
              'tea-label': true,
              checked: tea === chosenTea
            }"
          >
            <input
              id="tea"
              v-model="chosenTea"
              name="tea"
              type="radio"
              :value="tea"
            />
            <span>{{ tea }}</span>
          </label>
        </div>
        <button>Submit</button>
      </form>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      chosenTea: 'Earl Grey',
      teaTypes: {
        'Earl Grey': 'London',
        'Irish Breakfast': 'Dublin',
        Chai: 'Bombay',
        Rose: 'Atlantic City',
        Matcha: 'Tokyo',
        Rooibos: 'Cape Town',
        'Yerba Mate': 'Montreal',
        Green: 'Oregon Mist'
      }
    }
  },
  computed: {
    teaName() {
      return `${this.teaTypes[this.chosenTea]} Fog`
    },
    teaNames() {
      return Object.keys(this.teaTypes)
    }
  }
}
</script>
