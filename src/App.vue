<template>
  <v-app>
    <v-app-bar app>
      <v-app-bar-nav-icon @click="drawer = !drawer" />
      <v-toolbar-title> Cristina </v-toolbar-title>
      <v-spacer />
      <v-menu offset-y>
        <!-- <template v-slot:activator="{ on, attrs }"> -->
        <template #activator="{ on, attrs }">
          <v-btn icon v-bind="attrs" v-on="on">
            <v-icon>mdi-heart</v-icon>
          </v-btn>
        </template>

        <v-list>
          <v-list-item>
            <v-list-item-content>
              <v-list-item-title> Love 1 </v-list-item-title>
            </v-list-item-content>
          </v-list-item>
          <v-list-item>
            <v-list-item-content>
              <v-list-item-title> Love 2 </v-list-item-title>
            </v-list-item-content>
          </v-list-item>
          <v-list-item>
            <v-list-item-content>
              <v-list-item-title> Love 3 </v-list-item-title>
            </v-list-item-content>
          </v-list-item>
        </v-list>
      </v-menu>
    </v-app-bar>

    <v-navigation-drawer v-model="drawer" app>
      <v-list>
        <v-list-item
          @click="
            drawer = false;
            page = 'todo';
          "
        >
          <v-list-item-content>
            <v-list-item-title> Todo </v-list-item-title>
          </v-list-item-content>
        </v-list-item>
        <v-list-item
          @click="
            drawer = false;
            page = 'city-cafe';
          "
        >
          <v-list-item-content>
            <v-list-item-title> CityCafe </v-list-item-title>
          </v-list-item-content>
        </v-list-item>
        <v-list-item
          @click="
            drawer = false;
            page = 'image-viewer';
          "
        >
          <v-list-item-content>
            <v-list-item-title> ImageViewer </v-list-item-title>
          </v-list-item-content>
        </v-list-item>
        <v-list-item
          @click="
            drawer = false;
            page = 'table';
          "
        >
          <v-list-item-content>
            <v-list-item-title> Table </v-list-item-title>
          </v-list-item-content>
        </v-list-item>
      </v-list>
    </v-navigation-drawer>

    <v-main>
      <Todo v-if="page === 'todo'" />
      <CityCafe v-if="page === 'city-cafe'" />
      <ImageViewer v-if="page === 'image-viewer'" />
      <Table v-if="page === 'table'" />
    </v-main>
  </v-app>
</template>

<script>
import Todo from "./components/Todo";
import CityCafe from "./components/CityCafe";
import ImageViewer from "./components/ImageViewer";
import Table from "./components/Table";

export default {
  components: {
    Todo,
    CityCafe,
    ImageViewer,
    Table,
  },
  data() {
    return {
      drawer: false,
      page: "",
    };
  },
};
</script>
