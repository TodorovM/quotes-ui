<template>
    <div class="layout" :style="style">
        <Quote v-for="quote in data" :key="quote.id" :quote="quote" ref="quote" />
    </div>
</template>

<script>
    import Quote from './sub_component/Quote.vue'

    export default {
        name: 'layout',
        components: {
            Quote
        },
        data() {
            return {
                height: 0
            }
        },
        props: {
            data: {
                type: Array, 
            },
        },
        computed: {
            style() {
                return {
                    height: `${this.height}px`
                }
            }
        },
        updated(){
            const columns = [0, 0]
            const margin = getComputedStyle(this.$refs.quote[0].$el).marginTop.replace('px', '');
            this.$refs.quote.forEach((q, index) => {
                const order = index % 2 
                columns[order] += q.$el.offsetHeight;
            })
            this.height = Math.max(...columns) + ((this.$refs.quote.length / 2) * (margin * 2)) + 100 
        }
        
    }
</script>

<style lang="sass" scoped>
    .layout
        margin-top: 40px
        display: flex
        flex-flow: column wrap
</style>