<template>
    <div class="layout">
        <Quote v-for="quote in displayed" :key="quote.id" :quote="quote" ref="quote" />
    </div>
</template>

<script>
    import Quote from './sub_component/Quote.vue'
    import Masonry from 'masonry-layout'
    import EventBus from "../utils/eventBus"

    export default {
        name: 'layout',
        components: {
            Quote
        },
        data() {
            return {
                sorted: [],
                quotes: [],
                masonry: null
            }
        },
        computed: {
            displayed() {
                return this.sorted
            }
        },
        methods: {
            sort(category, descending) {
                this.sorted = this.sorted.sort((a,b) => a.participant[category].localeCompare(b.participant[category]))
                if (descending) this.sorted = this.sorted.reverse();
            },
            search(text) {
                this.sorted = this.quotes.filter(q => q.content.toLowerCase().includes(text.toLowerCase()))
            },
            remove(id){
                this.sorted = this.sorted.filter(q => q.id !== id)
                this.quotes = this.quotes.filter(q => q.id !== id)
            }
        },
        mounted(){
            EventBus.$on('data_loaded', (e) => {
                this.sorted = e;
                this.quotes = e;
                
                this.sort('nationality', false)
            });

            EventBus.$on('sort_items', ({category, descending}) => {
                this.sort(category, descending)
            })

            EventBus.$on('search', e => {
                this.search(e)
            })
            
            EventBus.$on('remove', e => {
                this.remove(e)
            })
        },
        updated() {
            if(!this.masonry) {
                this.masonry = new Masonry('.layout', { itemSelector: '.quote-block' })
            }
            this.masonry.reloadItems();
            this.masonry.layout()
        }
        
    }
</script>

<style lang="sass" scoped>
    .layout
        margin-top: 40px
</style>