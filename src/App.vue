<template>
  <v-app>


    <v-navigation-drawer temporary v-model="sidebar">
      <v-list>
        <v-list-tile
          v-for="item in menuItems" :key="item.title" :to="item.path">
          <v-list-tile-action>
            <v-icon>
              {{item.icon}}
            </v-icon>
          </v-list-tile-action>
          <v-list-tile-content>
            {{item.title}}
          </v-list-tile-content>
        </v-list-tile>
      </v-list>
    </v-navigation-drawer>


    <v-toolbar fixed>
      <span class="hidden-sm-and-up">
        <v-toolbar-side-icon @click.stop="sidebar = !sidebar">
        </v-toolbar-side-icon>
      </span>
      <v-toolbar-title>
      <router-link to="/" tag="span" style="cursor: pointer">
        {{appTitle}}
      </router-link>
      </v-toolbar-title>
      <v-spacer></v-spacer>
      <v-toolbar-items class="hidden-xs-only">
        <v-btn
          flat
          v-for="item in MenuItems" :key="item.title" :to="item.path">
          <v-icon left dark>
            {{item.icon}}
          </v-icon>
          {{item.title}}
          </v-btn>
    </v-toolbar-items>
    </v-toolbar>


    <main>
      <v-container fluid>
        <router-view>

        </router-view>
      </v-container>
    </main>


  </v-app>
</template>


<script>
  import VListTile from 'vuetify/src/components/VList/VListTile'
  import VListTileAction from 'vuetify/src/components/VList/VListTileAction'
  import VIcon from '../node_modules/vuetify/src/components/VIcon/VIcon.vue'
  import VToolbar from '../node_modules/vuetify/src/components/VToolbar/VToolbar.vue'
  import VBtn from '../node_modules/vuetify/src/components/VBtn/VBtn.vue'

  export default {
    components: {
      VBtn,
      VToolbar,
      VIcon,
      VListTileAction,
      VListTile},
    data () {
      return {
        appTitle: 'Classified Exchange App',
        sidebar: false,
        menuItems: [
          { title: 'Home', path: '/home', icon: 'home' },
          { title: 'Sign Up', path: '/signup', icon: 'face' },
          { title: 'Sign In', path: '/signin', icon: 'lock_open' }
        ]
      }
    }
  }
</script>


<style lang="stylus">
  @import './stylus/main'
</style>
