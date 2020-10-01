<template>
    <div :class="['sort', {selected: selected}]">
        Participant {{ category }}
        <ArrowDown :class="['arrow', {ascending: ascending}]" />
    </div>
</template>

<script>
    import ArrowDown from "@/assets/graphics/icons/arrow-down.svg";
    export default {
        name: "SortBy",
        components: {
            ArrowDown,
        },
        data() {
            return {
                selected: false,
                ascending: false,
            }
        },
        props: {
            category: {
                type: String
            }
        },
    }
</script>

<style lang="sass" scoped>
    .sort
        padding: 15px 20px
        background-color: white
        border-radius: 50px
        margin: 0 10px
        cursor: pointer
        @include boxShadow
        .arrow
            fill: $gray
            width: 20px
            vertical-align: middle
            transition: .5s
            transform-origin: center
            &.ascending
                transform: rotate(-180deg)
        &.selected
            color: $blue
            .arrow
                fill: $blue
</style>