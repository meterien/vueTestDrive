<template>
    <v-card class="ma-3 pa-3">
        <v-container>
            <v-layout class="row wrap">
                <v-flex xs-3 class="red pa-2 ma-2">
                    <v-avatar
                    tile
                    size="180"
                    color="grey lighten-4"
                    >
                    <img src="/apple-touch-icon-180x180.png" alt="avatar">
                    </v-avatar>
                </v-flex>
                <v-flex xs-9 class="blue pa-2 ma-2">
                    <v-input label="Name" v-text="name + ' ' + surName"></v-input>
                    <v-input v-text="country"></v-input>
                </v-flex>
            </v-layout>
        </v-container>
    </v-card>
</template>

<script>
export default {
    data: function() {
        return {
            name: 'Bob',
            surName: 'Vader',
            country: 'Canada',
        }
    }
}
</script>
