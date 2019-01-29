<template>
    <textarea id="editor" :value="value"
        v-on:input="updateValue($event.target.value)" >
    </textarea>
</template>

<script>
import ClassicEditor from '@ckeditor/ckeditor5-build-classic'

export default {
  name: 'Ckeditor',
  data: function () {
    return {
      instance: null
    }
  },
  props: ['value'],
  watch: {
    value () {
      let html = this.instance.getData()
      if (html !== this.value) {
        this.instance.setData(this.value)
      }
    }
  },
  mounted () {
    ClassicEditor
      .create(this.$el, {
        toolbar: ['bold', 'italic', 'link', 'bulletedList']
      })
      .then(editor => {
        this.instance = editor
        editor.model.document.on(change, () => { this.updateValue(editor.getData()) })
      })
      .catch(error => {
        console.error(error)
      })
  },
  methods: {
    updateValue: function (value) {
      this.$emit('input', value)
    }
  }
}
</script>
