<template>
    <v-container>
        <apollo-query :query="require('./../graphql/users/index.gql')">
            <template v-slot="{ result: {loading, error, data}}">
                <div v-if="loading">loading ...</div>
                <v-list three-one v-else-if="data" v-for="user in data.users" :key="user.userId">
                    <v-list-item>
                        <v-list-item-action>
                            <v-icon x-large>mdi-account</v-icon>
                        </v-list-item-action>
                        <v-list-item-content>
                            <v-list-item-title>{{user.username}}</v-list-item-title>
                            <v-list-item-subtitle>{{user.userId}}</v-list-item-subtitle>
                        </v-list-item-content>
                        <v-list-item-action>
                            <v-btn fab text><v-icon>mdi-pencil</v-icon></v-btn>
                        </v-list-item-action>
                        <v-list-item-action>
                            <v-btn fab text><v-icon>mdi-delete</v-icon></v-btn>
                        </v-list-item-action>
                    </v-list-item>
                </v-list>
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