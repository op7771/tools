<template>
  <v-app>
    <v-toolbar app dense color="blue darken-3" dark>
      <v-toolbar-title class="headline text-uppercase">
        <v-toolbar-side-icon @click.stop="drawer = !drawer"></v-toolbar-side-icon>
        <span>SAMSUNG </span>
        <span class="font-weight-light">Cardian</span>
      </v-toolbar-title>
      <v-spacer></v-spacer>
      <v-btn
        flat
        href="https://github.com/vuetifyjs/vuetify/releases/latest"
        target="_blank"
      >
        <span class="mr-2">Latest Release</span>
        <v-icon>mdi-open-in-new</v-icon>
      </v-btn>
    </v-toolbar>

    <v-navigation-drawer fixed temporary
                         :clipped="$vuetify.breakpoint.mdAndUp"
                         v-model="drawer"
    >
      <v-list class="pt-0" dense>
        <v-divider></v-divider>

        <v-list-tile
          v-for="item in items"
          :key="item.title"
          :to="item.link"
        >
          <v-list-tile-action>
            <v-icon>{{ item.icon }}</v-icon>
          </v-list-tile-action>

          <v-list-tile-content>
            <v-list-tile-title>{{ item.title }}</v-list-tile-title>
          </v-list-tile-content>
        </v-list-tile>
      </v-list>
    </v-navigation-drawer>
    <v-content>
      <router-view/>
    </v-content>
  </v-app>
</template>

<script>

export default {
  name: 'App',
  data () {
    return {
      drawer: false,
      items: [
        { title: 'Home', icon: 'mdi-view-dashboard', link: '/' },
        { title: 'About', icon: 'mdi-download', link: '/about' }
      ]
    }
  }
}
</script>
