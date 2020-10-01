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
            sort(category, ascending) {
                this.sorted = this.sorted.sort((a,b) => a.participant[category].localeCompare(b.participant[category]))
                if (ascending) this.sorted = this.sorted.reverse();
            }
        },
        mounted(){
            EventBus.$on('data_loaded', (e) => {
                this.sorted = e;
                this.quotes = e;
                
                this.sort('nationality', false)
            });

            EventBus.$on('sort_items', ({category, ascending}) => {
                this.sort(category, ascending)
            })
            
        },
        updated() {
            if(!this.masonry) {
                this.masonry = new Masonry('.layout', { itemSelector: '.quote-block' })
            }
            console.log()
            this.masonry.reloadItems();
            this.masonry.layout()
        }
        
    }
</script>

<style lang="sass" scoped>
    .layout
        margin-top: 40px
        display: flex
        flex-flow: column wrap
</style>