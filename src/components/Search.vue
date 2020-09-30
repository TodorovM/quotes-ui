<template>
    <div class="search">
        <div class="search-box">
            <Magnifier class="magnifier" />
            <input type="text" class="search-input" placeholder="Search">
        </div>
    </div>
</template>

<script>
    import Magnifier from '@/assets/graphics/icons/magnifier.svg'
    export default {
        name: 'Search',
        components: {
            Magnifier,
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
                &:focus
                    outline: none
</style>