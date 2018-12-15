<template>
  <div>
    <v-navigation-drawer app v-model="drawer">
      <v-list>
        <v-list-tile @click="route('/')">
          <v-list-tile-content>
            <v-list-tile-title>HOME</v-list-tile-title>
          </v-list-tile-content>
        </v-list-tile>
        <v-list-tile @click="route('/items')">
          <v-list-tile-content>
            <v-list-tile-title>ITEMS</v-list-tile-title>
          </v-list-tile-content>
        </v-list-tile>
      </v-list>
    </v-navigation-drawer>
    <v-toolbar app dark color="primary">
      <v-toolbar-side-icon  @click="drawer = !drawer"></v-toolbar-side-icon>
      <v-toolbar-title>Item Management System</v-toolbar-title>
    </v-toolbar>
  </div>
</template>

<script>
export default {
  data: function() {
    return {
      drawer: false
    };
  },
  methods: {
    route(url) {
      this.$router.push(url)
    }
  }
};
</script>
