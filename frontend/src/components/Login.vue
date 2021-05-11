<template>
<v-card
    class="mx-auto"
    max-width="400"
  >
    <v-toolbar
      color="cyan"
      dark
      flat
    >
      <v-toolbar-title>Social Network</v-toolbar-title>

      <v-spacer></v-spacer>
      <template v-slot:extension>
        <v-tabs
          v-model="tab"
          align-with-title
        >
          <v-tabs-slider color="yellow"></v-tabs-slider>

          <v-tab
            v-for="item in items"
            :key="item"
          >
            {{ item }}
          </v-tab>
        </v-tabs>
      </template>
    </v-toolbar>

    <v-tabs-items v-model="tab">
      <v-tab-item
        v-for="item in items"
        :key="item"
      >
        <v-card flat>
          <v-card-text v-show="item === 'Login'">
              <p>Login with your username and password:</p>
              <v-form>
                <v-text-field
                  outline
                  label="Username"
                  type="text"
                  v-model="username"></v-text-field>
                <v-text-field
                  outline
                  hide-details
                  label="Password"
                  type="password"
                  v-model="password"></v-text-field>
                <br>
                <v-btn color="info">
                  Login
                </v-btn>
              </v-form>
          </v-card-text>
          <v-card-text v-show="item === 'Sign Up'">
              <v-form>
                <v-text-field
                              outline
                              label="Username"
                              type="text"
                              v-model="username"></v-text-field>
                <v-text-field
                              outline
                              hide-details
                              label="Password"
                              type="password"
                              v-model="password"></v-text-field>
                <v-text-field
                              outline
                              hide-details
                              label="Password Confirmationn"
                              type="password"
                              v-model="passwordConfirmation"></v-text-field>
                              
                <br>
                <v-btn color="info">
                  Sign Up
                </v-btn>
              </v-form>
          </v-card-text>
        </v-card>
      </v-tab-item>
    </v-tabs-items>
  </v-card>

</template>

<script>
export default {
  name: 'Login',
  data: () => ({
      tab: null,
      items: [
        'Login', 'Sign Up',
      ],
      
      valid: false,
      username: '',
      usernameRules: [
        v => !!v || 'Username is required',
        v => v.length > 3 || 'Username must have more than 3 characters',
        v => v.length < 10 || 'Username must have less than 10 characters',
      ],
      email: '',
      emailRules: [
        v => !!v || 'E-mail is required',
        v => /.+@.+/.test(v) || 'E-mail must be valid',
      ],
      password: '',
      passwordRules: [
        v => !!v || 'Password is required',
        v => v.length > 3 || 'Password must have more than 3 characters',
        v => v.length < 10 || 'Password must have less than 10 characters',
      ],
      passwordConfirmation: '',
    }),
}
    
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
