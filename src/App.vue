<template>
    <div class="container">
        <appProgressBar :quoteCount="quotes.length" :maxQuotes="maxQuotes"></appProgressBar>
        <appNewQuote @quoteAdded="newQuote"></appNewQuote>
        <app-quote-grid :quotes="quotes" @quoteDeleted="deleteQuote"></app-quote-grid>
        <div class="row">
            <div class="col-sm-12 text-center">
                <div class="alert alert-info">Info: Click on a Quote to Delete it!</div>
            </div>
        </div>  
    </div>
</template>

<script>
    import QuoteGrid from './components/QuoteGrid.vue';
    import NewQuote from './components/NewQuote.vue';
    import Header from './components/Header.vue';

        export default {
            data: function(){
                return {
                    quotes: [
                        'Just a Quote to see something'
                    ],
                    maxQuotes: 10
                }
            },
            methods: {
                newQuote(quote){
                    if(this.quotes.length >= this.maxQuotes){
                        return alert('Please delete a quote first!')
                    }
                    this.quotes.push(quote);
                },
                deleteQuote(index){
                    this.quotes.splice(index, 1)
                }
            },
            components: {
                'app-quote-grid': QuoteGrid,
                appNewQuote: NewQuote,
                appProgressBar: Header
            }
        }
</script>

<style>
</style>
