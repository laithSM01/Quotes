<template>
  <div class="container">
    <app-header :maxQuotes="maxQuotes" :quoteCount="quotes.length"></app-header>
    <app-new-quote @sendToParent="handleChildQuote"></app-new-quote>
    <app-quote-grid :quotes="quotes" @delete="deleteQuote"></app-quote-grid>
    <div class="row">
      <div class="col-sm-12 text-center">
        <div class="alert alert-info">Click on a quote to delete it</div>
      </div>
    </div>
  </div>
</template>

<script>
import Header from './components/Header.vue'
import QuoteGrid from './components/QuoteGrid.vue'
import NewQuote from './components/NewQuote.vue'

export default {
  data() {
    return {
      quotes: [
        'just a quote to see something',
      ],
      maxQuotes: 10,
    }
  },
  components: {
    appQuoteGrid: QuoteGrid,
    appNewQuote: NewQuote,
    appHeader: Header
  },
  methods: {
    handleChildQuote(value) {
      // This method adds a new quote
      if(this.quotes.length >= this.maxQuotes) {
        return alert("you have reached your limits !")
      }
      this.quotes.push(value);
    },
    deleteQuote(index) {
      // This method deletes a quote at a specific index
      this.quotes.splice(index, 1);
    }
  }
}
</script>

<style>
/* Add your component styles here if needed */
</style>