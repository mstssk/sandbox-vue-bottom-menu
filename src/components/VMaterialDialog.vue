<template>
  <dialog ref="dialog" @click="onClickBackdrop" v-bind="$attrs" v-on="$listeners">
    <h3 class="header">
      <slot name="header"></slot>
    </h3>
    <div class="body">
      <slot></slot>
    </div>
    <div class="footer">
      <slot name="footer"></slot>
    </div>
  </dialog>
</template>

<script lang="ts">
import Vue from "vue";

export default Vue.component("v-material-dialog", {
  computed: {
    dialog: function() {
      return this.$refs["dialog"] as HTMLDialogElement;
    }
  },
  methods: {
    show() {
      this.dialog.showModal();
    },
    hide() {
      this.dialog.close();
    },
    onClickBackdrop(event: MouseEvent) {
      if (event.target === this.dialog) {
        this.hide();
      }
    }
  }
});
</script>

<style scoped lang="scss">
dialog {
  margin: 0;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  position: fixed;
  width: 500px;
  max-width: 90vw;
  border: none;
  box-shadow: 0 0 0.5rem black;
}

dialog::backdrop {
  background-color: rgba(0, 0, 0, 0.4);
}

.header {
  margin-top: 0;
  text-align: left;
}
.body {
  text-align: left;
  color: #424242;
}
.footer {
  text-align: right;

  button {
    text-transform: uppercase;
    font-weight: bold;
    margin: 0 0 0 8px;
    padding: 8px;
    width: 64px;
    border: none;
    &:hover {
      background: #00000022;
    }
  }
}
</style>
