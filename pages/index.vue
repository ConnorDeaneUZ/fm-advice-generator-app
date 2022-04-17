<template>
<section class="advice">

<div class="advice-container">

<p class="advice-heading">Advice #{{quoteNumber}}</p>

<p class="advice-quote">"{{quote}}"</p>
<img src="/pattern-divider-desktop.svg" alt="">
<button class="button" @click="fetchAdvice()"></button>

</div>
</section>
</template>

<script>
import axios from 'axios';

export default {
  name: 'IndexPage',

  data: () => ({
    quote: '',
    quoteNumber: ''
  }),

  created() {
    this.fetchAdvice();
  },

  methods: {
    fetchAdvice() {
      axios
      .get('https://api.adviceslip.com/advice')
      .then (res => {
        this.quote = res.data.slip.advice,
        this.quoteNumber = res.data.slip.id
      })
      .catch (
        console.log('No Advice Found')
      )
    }
  }

}

</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Manrope:wght@800&display=swap');

* {
  box-sizing: border-box;
  padding: 0;
  margin: 0;
  font-family: 'Manrope', sans-serif;
}

.advice {
  display: flex;
  justify-content: center;
  flex-direction: column;
  align-items: center;
  background-color: hsl(218, 23%, 16%);
  height: 100vh;
}

.advice-heading {
  color: #52feaa;
  text-transform: uppercase;
  letter-spacing: .2rem;
}

.advice-quote {
  font-size: 20px;
}

.advice-container {
  display: flex;
  flex-direction: column;
  justify-content: space-evenly;
  text-align: center;
  align-items: center;
  color: white;
  background-color: #303a49;
  width: 550px;
  height: 300px;
  border-radius: 10px;
  position: relative;
  padding: 20px;
box-shadow: rgba(0, 0, 0, 0.3) 0px 19px 38px, rgba(0, 0, 0, 0.22) 0px 15px 12px;
}

.button {
  position: absolute;
  border-radius: 50%;
  height: 70px;
  width: 70px;
  top: 260px;
  cursor: pointer;
  background-color: #52feaa;
  border: none;
  text-transform: uppercase;
  background-image: url('/icon-dice.svg');
  background-repeat: no-repeat;
  background-position: center;
}
</style>