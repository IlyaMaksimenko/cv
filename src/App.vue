<template>
  <v-app>
    <HelloDialog
      :visible="isHelloDialogVisible"
      name="username"
      @update:visible="updateHelloDialogVisible"
    />

    <v-main v-if="!showHi">
      <v-container fluid>
        <HelloWorld msg="Welcome to Your Vue.js + TypeScript App" />
      </v-container>
    </v-main>
  </v-app>
</template>

<script lang="ts">
import { Component, Vue } from "vue-property-decorator";
import HelloDialog from "./components/HelloDialog.vue";
import HelloWorld from "./components/HelloWorld.vue";

@Component({
  components: {
    HelloDialog,
    HelloWorld,
  },
})
export default class App extends Vue {
  isHelloDialogVisible = false;

  updateHelloDialogVisible(value: boolean) {
    this.isHelloDialogVisible = value;
  }

  mounted() {
    this.isHelloDialogVisible = true;
  }
}
</script>

<style lang="scss">
html {
  overflow-y: auto !important; // cause - https://github.com/vuetifyjs/vuetify/issues/1197;
}

body {
  margin: 0;
}
</style>
