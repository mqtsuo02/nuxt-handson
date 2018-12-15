<template>
  <v-app>
    <menu-list />
    <v-content>
      <v-container fluid>
        <nuxt />
      </v-container>
    </v-content>
  </v-app>
</template>

<script>
import MenuList from "~/components/MenuList";

export default {
  components: { MenuList }
};
</script>
