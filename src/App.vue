<template>
  <div class="main">
    <div class="columns is-gapless">
      <div class="column">
        <div class="editor-container">
          <editor text="Hello" :height="editorHeight" @change="updateFormatted"></editor>
        </div>
      </div>
      <div class="column">
        <div class="editor-container">
          <editor :text="text" :height="editorHeight"></editor>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import Vue from 'vue'
import Component from 'vue-class-component'
import Editor from './components/Editor.vue'

@Component({
  components: {
    Editor,
  }
})
export default class App extends Vue {
  editorHeight = 600

  text = ''

  updateFormatted(text) {
    this.text = text
  }
}
</script>

<style lang="scss">
@import "bulma/sass/utilities/_all.sass";
@import "bulma/sass/grid/columns.sass";

html,
body {
  margin: 0;
  padding: 0;
}
</style>

<style lang="scss" scoped>
.main {
  width: 100%;
  position: relative;
}
.columns {
}
.editor-container {
  margin: 10px;
}
</style>
