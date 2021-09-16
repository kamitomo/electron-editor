<template>
  <div>
    <button @click="openFile">開く</button>
    <button @click="saveFile">保存</button>
    <div class="mainArea">
      <textarea
        placeholder="本文を入力してください。"
        rows="20"
        cols="100"
        v-model="text"
        class="textArea"
      />
    </div>
  </div>
</template>

<script>
import { ipcRenderer } from 'electron'

export default {
  name: 'Editor',
  data() {
    return {
      text: '',
    }
  },
  methods: {
    async openFile() {
      const { canceled, data } = await ipcRenderer.invoke('open-file-dialog')
      if (canceled) return
      this.text = data
    },
    async saveFile() {
      const data = this.text
      await ipcRenderer.invoke('save-file-dialog', data)
    },
  },
}
</script>
