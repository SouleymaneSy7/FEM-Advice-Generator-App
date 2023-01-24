<template>
  <main>
    <section class="card">
      <h1 class="card__title">Advice # {{ advice.id }}</h1>

      <p class="card__textbox">"{{ advice.advice }}"</p>

      <div class="card__images">
        <img
          src="../assets/pattern-divider-desktop.svg"
          alt="Pattern Divider"
        />
      </div>

      <button v-on:click="generateAdvice" class="card--btn">
        <img src="../assets/icon-dice.svg" alt="Dice Icons" />
      </button>
    </section>

    <footer class="attribution">
      <div>
        <p>
          Challenge by
          <a href="https://www.frontendmentor.io?ref=challenge" target="_blank"
            >Frontend Mentor</a
          >
        </p>

        <p>
          Coded <span>♥</span> by
          <a href="https://github.com/SouleymaneSy7" target="_blank"
            >Souleymane Sy</a
          >
        </p>
      </div>
    </footer>
  </main>
</template>

<script>
import axios from "axios";

export default {
  name: "AdviceCard",
  data() {
    return {
      advice: "",
    };
  },
  mounted() {
    axios.get("https://api.adviceslip.com/advice").then((response) => {
      let res = response.data.slip;

      this.advice = res;
    });
  },
  methods: {
    generateAdvice() {
      axios.get("https://api.adviceslip.com/advice").then((response) => {
        let res = response.data.slip;

        this.advice = res;
      });
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
// colors
$light-cyan: hsl(193, 38%, 86%);
$neon-green: hsl(150, 100%, 66%);
$grayish-blue: hsl(217, 19%, 38%);
$dark-grayish-blue: hsl(217, 19%, 24%);

.card {
  position: relative;
  max-width: 32.5rem;
  background: $dark-grayish-blue;
  border-radius: 0.625rem;
  padding: 3.125rem;
}

.card__title {
  font-size: 0.8125rem;
  font-weight: 500;
  color: $neon-green;
  letter-spacing: 4px;
  text-transform: uppercase;
  text-align: center;

  margin-bottom: 1.5625rem;
}

.card__textbox {
  font-size: 1.5625rem;
  font-weight: 600;
  color: $light-cyan;
  text-align: center;
  margin-block: 1.25rem;
}

.card__images {
  width: 100%;
  display: flex;
  justify-content: center;
  margin-bottom: 1.25rem;

  img {
    max-width: 100%;
    height: auto;
    cursor: pointer;
  }
}

.card--btn {
  width: 3.75rem;
  height: 3.75rem;

  position: absolute;
  bottom: -1.875rem;
  left: 50%;
  transform: translateX(-50%);

  display: flex;
  justify-content: center;
  align-items: center;

  border: none;
  outline: none;

  background: $neon-green;
  border-radius: 50%;

  transition: box-shadow 500ms;

  cursor: pointer;

  &:hover {
    box-shadow: 0 0 2.5rem $neon-green;
  }
}

.attribution {
  text-align: center;
  margin-top: 7rem;

  & div p {
    color: $light-cyan;
  }

  & div span {
    font-size: 1.75rem;
    color: $neon-green;
  }

  & div a {
    font-size: 1.25rem;
    color: $neon-green;
    text-decoration: none;

    transition: 300ms;

    &:hover {
      text-decoration: underline;
    }
  }
}
</style>
