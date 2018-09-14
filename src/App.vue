<template>
  <v-app>
    <v-navigation-drawer
      v-model="drawer"
      enable-resize-watcher
      clipped
      temporary
      app
    >
      <v-list>
        <v-list-tile
          value="true"
          v-for="(item, i) in items"
          :key="i"
        >
          <v-list-tile-action>
            <v-icon v-html="item.icon"></v-icon>
          </v-list-tile-action>
          <v-list-tile-content>
            <v-list-tile-title v-text="item.title"></v-list-tile-title>
          </v-list-tile-content>
        </v-list-tile>
      </v-list>
    </v-navigation-drawer>
    <v-toolbar
      app
      :clipped-left="clipped"
    >
      <v-toolbar-side-icon @click.stop="drawer = !drawer"></v-toolbar-side-icon>
      <v-toolbar-title v-text="title"></v-toolbar-title>
    </v-toolbar>
    <v-content>
      <Form1/>
      <Profile/>
    </v-content>
    <v-footer :fixed="fixed" app>
      <span>&copy; 2018</span>
    </v-footer>
  </v-app>
</template>

<script>
import Form1 from './components/Form1'
import Profile from './components/Profile'

export default {
  name: 'App',
  components: {
    Form1,
    Profile
  },
  data () {
    return {
      drawer: false,
      items: [{
        icon: 'bubble_chart',
        title: 'Dashboard'
      }],
      title: 'Dev project'
    }
  }
}
</script>
