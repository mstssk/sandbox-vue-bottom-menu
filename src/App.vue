<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png" />
    <HelloWorld msg="Welcome to Your Vue.js + TypeScript App" />
    <button @click="$refs.menu.show()">開く</button>
    <v-bottom-menu ref="menu">
      <ul>
        <li>テスト</li>
        <li><button @click="alert">alert</button></li>
      </ul>
      <button @click="$refs.menu.hide()">キャンセル</button>
    </v-bottom-menu>
  </div>
</template>

<script lang="ts">
import { Component, Vue } from "vue-property-decorator";
import HelloWorld from "./components/HelloWorld.vue";
import VBottomMenu from "./components/VBottomMenu.vue";

@Component({
  components: {
    HelloWorld,
    VBottomMenu,
  }
})
export default class App extends Vue {
  open = false;

  alert(){
    alert(1);
  }

}
</script>

<style lang="scss">
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
