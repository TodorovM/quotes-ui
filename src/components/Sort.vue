<template>
    <div class="sort-container" @click="click">
        <p class="sort-label">Sort by: </p>
        <SortBy v-for="(category, index) in categories" :key="index" :category="category" ref="sort" />
    </div>
</template>

<script>
    import SortBy from "./sub_component/SortBy"
    export default {
        name: 'Order',
        data() {
            return {
                categories: ['nationality', 'name'],
                sortingBy: 'nationality'
            }
        },
        components: {
            SortBy,
        },
        methods: {
            click(e) {
                const item = this.$refs.sort.find(({$el}) => $el === e.target)
                const selected = this.$refs.sort.find(el => el.selected)
                if (item) {
                    item.selected = true;
                    if(selected !== item) selected.selected = false;
                    this.sortingBy = item.category;
                    item.ascending = !item.ascending;
                    }
            }
        },
        mounted () {
            this.$refs.sort.find(el => el.category === this.sortingBy).selected = true;

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