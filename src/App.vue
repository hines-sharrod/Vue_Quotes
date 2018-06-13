<template>
    <div class="container">
      <app-header :quoteCount="quotes.length" :maxQuotes="maxQuotes"></app-header>
      <app-add-quote @quoteAdded="addedQuote"></app-add-quote>
      <app-quote-display :quotesArray="quotes" @quoteDeleted="quoteDeleted"></app-quote-display>
      <div class="alert alert-info">Info: Click on a Quote to delete it</div>
      <div id="quoteWarning"></div>
    </div>
</template>

<script>
import Header from "./components/Header.vue";
import AddQuote from "./components/AddQuote.vue";
import QuoteDisplay from "./components/QuoteDisplay.vue";

export default {
  data: function() {
    return {
      quotes: ["Just something to see for now"],
      maxQuotes: 10
    };
  },
  methods: {
    addedQuote(quote) {
      if (this.quotes.length >= this.maxQuotes) {
        return (document.getElementById("quoteWarning").innerHTML =
          '<div class="alert alert-warning" role="alert"> <strong>Warning!</strong> Please Delete some of the existing Quotes first!</div>');
      }
      this.quotes.push(quote);
    },
    quoteDeleted(index) {
      this.quotes.splice(index, 1);
      return (document.getElementById("quoteWarning").innerHTML = "");
    }
  },
  components: {
    appHeader: Header,
    appAddQuote: AddQuote,
    appQuoteDisplay: QuoteDisplay
  }
};
</script>

<style scoped>
#quoteWarning {
  position: absolute;
  top: 0;
  right: 0;
}

.alert-info {
  text-align: center;
}
</style>
