<template>
  <div ref="editor" class="editor" :style="{height: `${height}px`}"></div>
</template>

<script>
import Vue from 'vue'
import Component from 'vue-class-component'
import { editor } from 'monaco-editor'

@Component({
  props: {
    text: String,
    height: Number,
  }
})
export default class Editor extends Vue {

  editor = undefined

  mounted() {
    this.editor = editor.create(this.$refs.editor, {
      value: this.text,
      minimap: {
        enabled: false,
      },
      theme: 'vs-dark',
    })

    this.editor.onDidChangeModelContent(e => {
      this.$emit('change', this.editor.getValue());
    })
  }
}
</script>

<style lang="scss" scoped>
</style>

