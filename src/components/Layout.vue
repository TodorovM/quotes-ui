<template>
    <div class="layout">
        <Quote :quote="quoteData" />
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
                quoteData: {
                    "id": "5e25adf5ca150f293e0e8e23",
                    "content": "So I use a lot of 409",
                    "type": "QUOTE",
                    "tags": ["middle", "test"],
                    "studies": [158],
                    "created_by": {
                        "name": "Admin",
                        "surname": "Adminov",
                        "email": "admin@usertrb.net",
                        "client_id": 1046,
                        "client": { "id": 1046, "name": "UserTribe" }
                    },
                    "video": { "id": 330 },
                    "start_timestamp": 67.5,
                    "end_timestamp": 69.2,
                    "start": 67.5,
                    "end": 69.2,
                    "participant": {
                        "id": 474,
                        "name": "Notcopied",
                        "email": "notcopied@aaa.com",
                        "nationality": "Bangladesh",
                        "age": 34
                    }
                }
            }
        },
        
    }
</script>

<style lang="sass" scoped>
    .layout
        @include center($max-width, $min-width)
</style>