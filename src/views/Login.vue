<template>
    <v-app id="inspire">
        <v-content>
            <v-container fluid fill-height>
                <v-layout align-center justify-center>
                    <v-flex xs12 sm8 md4>
                        <v-card class="elevation-12">
                            <v-toolbar dark color="primary">
                                <v-toolbar-title>Login form</v-toolbar-title>
                                <v-spacer></v-spacer>
                            </v-toolbar>
                            <v-card-text>
                                <form ref="form" action="" method="post">
                                    <v-text-field prepend-icon="person" name="loginId" label="Login" type="text"></v-text-field>
                                    <v-text-field id="password" prepend-icon="lock" name="loginpw" label="Password" type="password"></v-text-field>
                                </form>
                            </v-card-text>
                            <v-card-actions>
                                <v-spacer></v-spacer>
                                <v-btn color="primary" @click="submit">Login</v-btn>
                            </v-card-actions>
                        </v-card>
                    </v-flex>
                </v-layout>
            </v-container>
        </v-content>
    </v-app>
</template>

<script>
export default {
  data: () => ({
    drawer: null
  }),
  props: {
    source: String
  },
  mounted () {
    console.log('x')
  },
  methods: {
    submit () {
      this.$refs.form.submit()
    }
  }
}
</script>
