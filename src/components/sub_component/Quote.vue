<template>
    <div class="quote-block">
        <div class="top">
            <QuotationMark class="quotation-mark" />
            <Close class="close-btn" @mousedown="remove"/>
        </div>
        <div class="quote-content">
            <div class="quote-text"> {{ quote.content }} </div>
            <div class="tags">
                <span v-for="(tag, index) in quote.tags" :key="index" class="tag">{{ tag }}</span>
            </div>
            <div class="bottom">{{ quote.participant.name }}, {{quote.participant.age}} from {{quote.participant.nationality}}  </div>
        </div>
    </div>
</template>

<script>
    import QuotationMark from '@/assets/graphics/icons/quote.svg'
    import Close from '@/assets/graphics/icons/x.svg';
    import EventBus from '../../utils/eventBus'
    export default {
        name: 'quote',
        components: {
            QuotationMark,
            Close
        },
        props: {
            quote: {
                type: Object
            }
        },
        methods: {
            remove() {
                EventBus.$emit('remove', this.quote.id)
            }
        },
    }
</script>

<style lang="sass" scoped>

    .quote-block
        width: calc(#{100% / $number-of-columns} - #{$number-of-columns * $margins})
        min-width: 320px
        margin: $margins
        background-color: white
        padding: 26px
        border-radius: 10px
        @include boxShadow
        &:nth-child(odd)
            order: 1
        &:nth-child(even)
            order: 2
        .top
            height: 33px
            display: flex
            justify-content: space-between
            .quotation-mark
                fill: $blue
                height: 100%
            .close-btn
                height: 80%
                cursor: pointer
        .quote-content
            padding: 22px 22px 7px
            .quote-text
                font-size: 21px
                margin: 10px 0
            .tags
                margin: 43px 0 47px
                .tag
                    padding: 10px
                    border-radius: 30px
                    border: 1px solid $gray
                    margin-right: 11px
                    font-size: 14px
                    font-weight: 200
                    color: $gray
            .bottom
                color: $gray
                font-size: 14px
                
</style>