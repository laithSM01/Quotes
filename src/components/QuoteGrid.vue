<template>
    <div class="row" >
        <app-quote v-for="(quote, index) in quotes" :key="quote" @click.native="handleComponentClick(index)">
        {{ quote }}
        </app-quote>

    </div>
</template>

<script>
import Quote from './Quote.vue';
import NewQuote from './NewQuote.vue'

export default ({
    props: ['quotes'],
    components: {
        appQuote: Quote,
    },
    methods: {
        handleComponentClick(index) {
            this.$emit('delete', index)
        }
    }
})
</script>
