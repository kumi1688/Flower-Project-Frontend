<template>
  <v-app id="inspire">
    <v-navigation-drawer
            v-model="drawer"
            app
            clipped
    >
    <sidebar></sidebar>
    </v-navigation-drawer>

    <v-app-bar
            app
            clipped-left
    >
      <v-app-bar-nav-icon @click.stop="drawer = !drawer" />
      <v-toolbar-title>원예 도우미</v-toolbar-title>
    </v-app-bar>

    <v-content>
      <v-container
              class="fill-height"
              fluid
      >
        <v-row
                align="center"
                justify="center"
        >
      <sensor></sensor>

        </v-row>
      </v-container>
    </v-content>

    <v-footer app>
      <span>&copy; 2019</span>
    </v-footer>
  </v-app>
</template>

<script>
  import SideBar from "./components/SideBar";
  import SensorContainer from "./components/container/SensorContainer";


  export default {
    props: {
      source: String,
    },
    components:{
      'sidebar': SideBar,
      'sensor':  SensorContainer,
    },
    data: () => ({
      drawer: null,
    }),

    created () {
      this.$vuetify.theme.white = true
    },
  }
</script>
