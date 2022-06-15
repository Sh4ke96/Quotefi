<template>
  <div class="app">
    <Header title="Quotefi Application" />
    <Quote :quote="quote" />
    <div class="button__container">
      <button @click="getQuote">Generate</button>
    </div>
    <QuoteList :quotes="quotes" />
  </div>
</template>

<script>
import Header from "./components/Header.vue";
import Quote from "./components/Quote.vue";
import QuoteList from "./components/QuoteList.vue";

export default {
  name: "App",
  components: {
    Header,
    Quote,
    QuoteList,
  },
  data() {
    return {
      quote: {},
      quotes: [],
    };
  },
  methods: {
    async getQuote() {
      if (this.quote.content) {
        this.quotes = [...this.quotes, this.quote];
      }

      const data = await fetch("https://animechan.vercel.app/api/random").then(
        (res) => res.json()
      );

      this.quote = {
        content: data.quote,
        anime: data.anime,
        character: data.character,
      };
    },
  },
  created() {
    this.getQuote();
  },
};
</script>

<style lang="scss">
:root {
  --primary: #f15412;
  --secondary: #34b3f1;
  --dark: #131a26;
  --light: #eee;
  --grey: #848484;
}

* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-family: "Fira Sans", sans-serif;
}

.button__container {
  display: flex;
  justify-content: center;
  padding: 0px 32px;
  margin: 64px auto;

  button {
    border: none;
    outline: none;
    background-color: var(--secondary);
    padding: 16px 32px;
    border-radius: 99px;
    color: var(--light);
    font-size: 28px;
    font-weight: 700;
    text-transform: uppercase;
    cursor: pointer;
    transition: 0.4s;

    &:hover {
      background-color: var(--primary);
    }
  }
}
</style>
