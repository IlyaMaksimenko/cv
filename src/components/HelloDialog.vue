<template>
  <v-dialog
    v-model="syncedVisible"
    fullscreen
    hide-overlay
    transition="dialog-top-transition"
  >
    <div
      class="hello-dialog-content"
      @wheel.prevent.stop="onWheel"
      @touchmove.prevent.stop="onTouchMove"
    >
      <h1>Hello!</h1>
      <h2>My name is {{ name }}!</h2>
      <v-btn
        @click="hide"
        class="my-4"
      >
        Hi!
      </v-btn>
    </div>
  </v-dialog>
</template>

<script lang="ts">
import { Component, Prop, PropSync, Vue } from "vue-property-decorator";

@Component
export default class HelloDialog extends Vue {
  @PropSync("visible", { type: Boolean }) syncedVisible!: boolean;
  @Prop() name!: string;

  hide() {
    this.syncedVisible = false;
  }

  onTouchMove() {
    this.hide();
  }

  onWheel() {
    this.hide();
  }
}
</script>

<style
  lang="scss"
  scoped
>
.hello-dialog-content {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  background-color: #fff;
  width: 100%;
  height: 100%;

  h1,
  h2,
  h3 {
    font-weight: 300;
  }

  button {
    text-transform: none;
  }
}
</style>
