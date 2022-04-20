<template>
  <v-app>
    <HelloDialog
      :visible="isHelloDialogVisible"
      name="username"
      @update:visible="updateHelloDialogVisible"
    />
    <iframe
      class="frame"
      src="/cv.html"
    />
    <BottomPanel name="username" />
  </v-app>
</template>

<script lang="ts">
import { Component, Vue } from "vue-property-decorator";
import HelloDialog from "./components/HelloDialog.vue";
import BottomPanel from "./components/BottomPanel.vue";

@Component({
  components: {
    HelloDialog,
    BottomPanel,
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

.frame {
  width: 100%;
  height: 100%;
  border: 0;
}
</style>
