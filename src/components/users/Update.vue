<template>
    <div>
        <v-btn @click="dialog = true" fab text><v-icon>mdi-pencil</v-icon></v-btn>
        <v-dialog v-model="dialog" max-width="500px">
            <v-card>
            <v-card-title>
                Update User
            </v-card-title>
            
                
                <apollo-mutation :mutation="require('./../../graphql/users/update.gql')" :variables="{userId: user.userId, patchUserInfo}" @done="patchUser">
                    <template v-slot="{ mutate, loading, error }">
                        <v-card-text>
                            <v-text-field 
                                    class="mt-5" 
                                    prepend-inner-icon="mdi-account" 
                                    label="username" 
                                    color="success"
                                    outlined 
                                    value="water"
                                    clearable
                                    v-model="patchUserInfo.username"
                            ></v-text-field>
                        </v-card-text>
                        <v-card-actions>
                            <v-btn @click="mutate()" text>UPDATE</v-btn>
                            <v-btn color="primary" text @click="dialog = false">Close</v-btn>
                        </v-card-actions>
                    </template>
                </apollo-mutation>
            
            
            </v-card>
        </v-dialog>
    </div>
</template>

<script>
export default {
    name:'update',
    props:{
        user: null
    },
    data(){
        return {
            show: null,
            dialog: null,
            patchUserInfo: {
                username: this.user.username,
            }
        }
    }, 
    methods: {
        patchUser(val){
            this.value = val
        }, 
    }
}
</script>