<template>
    <div class="layout">
        <Quote v-for="quote in data" :key="quote.id" :quote="quote" ref="quote" />
    </div>
</template>

<script>
    import Quote from './sub_component/Quote.vue'
    import Masonry from 'masonry-layout'

    export default {
        name: 'layout',
        components: {
            Quote
        },
        props: {
            data: {
                type: Array, 
            },
        },
        updated(){
            new Masonry('.layout', {
                itemSelector: '.quote-block',
            })
        }
        
    }
</script>

<style lang="sass" scoped>
    .layout
        margin-top: 40px
        display: flex
        flex-flow: column wrap
</style>