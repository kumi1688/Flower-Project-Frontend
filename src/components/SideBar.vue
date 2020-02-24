<template>
    <v-list dense>
        <v-list-item link>
            <v-list-item-action>
                <v-icon>mdi-oil-temperature</v-icon>
            </v-list-item-action>
            <v-list-item-content>
                <v-list-item-title>센서 확인</v-list-item-title>
            </v-list-item-content>
        </v-list-item>
        <v-list-item link>
            <v-list-item-action>
                <v-icon>mdi-book</v-icon>
            </v-list-item-action>
            <v-list-item-content>
                <v-list-item-title>일지 작성</v-list-item-title>
            </v-list-item-content>
        </v-list-item>
        <v-list-item link>
            <v-list-item-action>
                <v-icon>mdi-search-web</v-icon>
            </v-list-item-action>
            <v-list-item-content>
                <v-list-item-title>일지 검색</v-list-item-title>
            </v-list-item-content>
        </v-list-item>
    </v-list>
</template>

<script>


    export default {
        name: "SideBar"
    }
</script>

<style scoped>

</style>
