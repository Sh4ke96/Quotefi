<template>
  <div class="app">
    <Header title="Quotefi Application"/>
    <Quote :quote="quote"/>
  </div>
</template>

<script>
import Header from './components/Header.vue';
import Quote from './components/Quote.vue';

export default {
  name: "App",
  components: {
    Header,
    Quote
  },
  data() {
    return {
      quote: {
        content: 'Content goes here',
        anime: 'Naruto',
        character: 'Bobuszko'
      },
      quotes: []
    }
  }
};
</script>

<style lang="scss">
:root {
  --primary: #F15412;
  --secondary:#34B3F1;
  --dark: #131A26;
  --light: #EEE;
  --grey: #848484;
}

* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-family: 'Fira Sans', sans-serif;
}
</style>
