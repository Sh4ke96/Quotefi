<template>
  <section class="qoute-list">
    <h2 class="quote-title">Quotes List</h2>
    <div class="quote" v-for="(quote, i) in quotes.slice().reverse()" :key="i">
      <div class="quote-content">
        {{ quote.content }}
      </div>
    </div>
  </section>
</template>

<script>
export default {
  props: ["quotes"],
};
</script>

<style lang="scss" scoped>
.qoute-list {
  padding: 32px;
  max-width: 720px;
  margin: 0 auto;

  .quote-title {
    font-size: 32px;
    max-width: 250px;
    margin: 0 auto 32px auto;
    color: var(--dark);
    font-weight: 700;
    text-align: center;
    text-transform: uppercase;
    padding-bottom: 8px;
    border-bottom: 5px solid var(--primary);
  }

  .quote {
    background-color: var(--light);
    padding: 16px;
    border-radius: 16px;
    margin-bottom: 16px;

    &-content {
      overflow: hidden;
      text-overflow: ellipsis;
      white-space: nowrap;
      line-height: 18px;
      max-height: 18px;
      transition: 0.4s;
    }

    &:hover {
      .quote-content {
        white-space: unset;
        max-height: unset;
        cursor: pointer;
      }
    }
  }
}
</style>