<template>
  <dialog ref="dialog" @click="onClickBackdrop" v-bind="$attrs" v-on="$listeners">
    <slot></slot>
  </dialog>
</template>

<script lang="ts">
// https://developer.mozilla.org/ja/docs/Web/API/HTMLDialogElement
// https://jp.vuejs.org/v2/guide/components-custom-events.html
import { Component, Prop, Watch, Vue } from "vue-property-decorator";

@Component({
  name: "v-bottom-menu"
})
export default class VBottomMenu extends Vue {
  show() {
    this.dialog.showModal();
  }

  hide() {
    this.dialog.close();
  }

  onClickBackdrop(event: MouseEvent) {
    if (event.target === this.dialog) {
      this.hide();
    }
  }

  get dialog() {
    return this.$refs["dialog"] as HTMLDialogElement;
  }
}
</script>

<style scoped lang="scss">
dialog {
  padding: 0;
  margin: 0;

  bottom: 0;
  position: fixed;
  width: 100vw;
  max-width: 640px;

  border: none;
  box-shadow: 0 0 1em black;
}

dialog::backdrop {
  background-color: rgba(0, 0, 0, 0.4);
}
</style>
