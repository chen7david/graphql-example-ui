<template>
    <div>
        <v-btn rounded @click="dialog = true">
            <v-icon>mdi-plus</v-icon>
        </v-btn>

        <v-dialog v-model="dialog" max-width="500px">
            <v-card>
            <v-card-title>
                New User 
            </v-card-title>
            <v-card-text>
                <apollo-mutation :mutation="require('./../../graphql/users/create.gql')" :variables="{addUserInfo}" @done="addUser">
                    <template v-slot="{ mutate, loading, error }">
                        <v-text-field 
                                class="mt-5" 
                                prepend-inner-icon="mdi-account" 
                                label="username" 
                                color="success"
                                outlined 
                                clearable
                                v-model="addUserInfo.username"
                        ></v-text-field>

                        <v-text-field 
                                prepend-inner-icon="mdi-lock" 
                                label="password" 
                                color="success"
                                outlined 
                                clearable
                                @click:append="show = !show"
                                :type="show ? 'text' : 'password'"
                                :append-icon="show ? 'mdi-eye' : 'mdi-eye-off'"
                                v-model="addUserInfo.password"
                        ></v-text-field>
                        <v-btn @click="mutate()">CREATE</v-btn>
                    </template>
                </apollo-mutation>
            </v-card-text>
            <v-card-actions>
                <v-btn color="primary" text @click="dialog = false">
                    Close
                </v-btn>
            </v-card-actions>
            </v-card>
        </v-dialog>
    </div>
</template>

<script>
export default {
    name:'update',
    data(){
        return {
            show: null,
            dialog: null,
            addUserInfo: {
                username:'',
                password:''
            }
        }
    }, 
    methods: {
        addUser(val){
            this.value = val
        }, 
    }
}
</script>