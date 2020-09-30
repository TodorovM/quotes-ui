<template>
    <div class="sort-container">
        <p class="sort-label">Sort by: </p>
        <SortBy v-for="(category, index) in categories" :key="index" :category="category" />
    </div>
</template>

<script>
    import SortBy from "./sub_component/SortBy"
    export default {
        name: 'Order',
        data() {
            return {
                categories: ['nationality', 'name']
            }
        },
        components: {
            SortBy,
        },
    }
</script>

<style lang="sass" scoped>
    .sort-container
        width: 100%
        @include centerElements
        margin-top: 21px
        font-size: 15px
        .sort-label
            color: $gray
</style>