<template>
    <div>
        <v-btn @click="dialog = true" fab text><v-icon>mdi-delete</v-icon></v-btn>
        <v-dialog v-model="dialog" max-width="500px">
            <v-card>
            <v-card-title>
                Delete {{user.userId}} 
            </v-card-title>
            <v-card-text>
                Are you sure you would like to delete {{user.username}}, you will not be able to reverse this change.
            </v-card-text>
            <v-card-actions>
                <apollo-mutation :mutation="require('./../../graphql/users/delete.gql')" :variables="{userId: user.userId}" @done="deleteUser">
                    <template v-slot="{ mutate, loading, error }">
                        <v-btn @click="mutate()" text class="red--text" >DELETE</v-btn>
                    </template>
                </apollo-mutation>
                <v-btn color="primary" text @click="dialog = false">Close</v-btn>
            </v-card-actions>
            </v-card>
        </v-dialog>
    </div>
</template>

<script>
export default {
    name:'delete',
    props:{
        user: null
    },
    data(){
        return {
            dialog: null,
        }
    }, 
    methods: {
        deleteUser(val){
            this.value = val
        }, 
    }
}
</script>