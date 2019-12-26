<template>
    <v-container>
        <apollo-query :query="require('./../graphql/users/index.gql')">
            <template v-slot="{ result: {loading, error, data}}">  
                {{data}}
            </template>
        </apollo-query>
    </v-container>
</template>


<script>

export default {
    name:'Students',
    components: {

    }
}
</script>