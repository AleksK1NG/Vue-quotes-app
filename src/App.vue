<template>
    <div class="container">
        <app-header :quoteCount="quotes.length" :maxQuotes="maxQuotes"></app-header>
        <new-quote @quoteAdded="newQuote"></new-quote>
        <quote-grid :quotes="quotes" @deleteQuote="deleteQuote"></quote-grid>
      <div class="row">
        <div class="col-sm-12 text-center">
          <div class="alert alert-info">
             <h5>Click on Quote to delete it !</h5>
          </div>
        </div>
      </div>
    </div>
</template>

<script>
  import QuoteGrid from './components/QuoteGrid.vue';
  import Quote from './components/Quote.vue';
  import NewQuote from './components/NewQuote.vue';
  import Header from './components/Header.vue'
    export default {
        data(){
          return{
            maxQuotes: 10,
            quotes: ['Work hard go pro !']
          }
        },
      methods:{
        newQuote(quote){
          if (this.quotes.length >= this.maxQuotes) {
            return alert('Please delete Quotes !');
          }
          this.quotes.push(quote);
        },
        deleteQuote(index){
          this.quotes.splice(index, 1);
        }
      },
      components:{
        quoteGrid: QuoteGrid,
        quote: Quote,
        newQuote: NewQuote,
        appHeader: Header
      },
    }
</script>

<style>
</style>
