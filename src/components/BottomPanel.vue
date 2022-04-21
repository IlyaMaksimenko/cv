<template>
  <v-bottom-navigation
    mandatory
    color="purple"
  >
    <v-btn
      href="/cv.pdf"
      :download="filename"
    >
      <span>Download PDF</span>
      <v-icon>mdi-file-pdf-box</v-icon>
    </v-btn>
  </v-bottom-navigation>
</template>

<script lang="ts">
import { Component, Prop, Vue } from "vue-property-decorator";

@Component
export default class HelloDialog extends Vue {
  @Prop() name!: string;

  get filename() {
    const now = new Date();
    const timestamp = `${now.getDate()}-${now.getMonth()}-${now.getFullYear()}`;
    const username = this.name.replaceAll(" ", "_");
    return `${username}_${timestamp}.pdf`;
  }
}
</script>
