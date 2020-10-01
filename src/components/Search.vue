<template>
    <div class="search">
        <div class="search-box">
            <Magnifier class="magnifier" />
            <input v-model="inputData" type="text" class="search-input" placeholder="Search" @keyup="search">
        </div>
    </div>
</template>

<script>
    import Magnifier from '@/assets/graphics/icons/magnifier.svg'
    import EventBus from "../utils/eventBus"
    export default {
        name: 'Search',
        components: {
            Magnifier,
        },
        data() {
            return {
                inputData: ""
            }
        },
        methods: {
            search() {
               EventBus.$emit('search', this.inputData)
            }
        },
    }
</script>

<style lang="sass" scoped>
    .search
        width: 100%
        @include centerElements
        .search-box
            background-color: white
            width: 48%
            display: flex
            height: 73px
            margin-top: 27px
            padding: 0 14px
            border-radius: 50px
            @include boxShadow
            .magnifier
                width: 38px
                fill: $gray
            .search-input
                padding: 0 11px
                font-size: 20px
                border: 0
                font-weight: 200
                font-family: inherit
                width: 60%
                text-overflow: ellipsis
                &:focus
                    outline: none
</style>