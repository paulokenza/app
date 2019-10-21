<template>
  <div class="interface-wysiwyg">
    <Editor
      ref="editorElement"
      :init="initOptions"
      :value="value"
      @onKeyUp="updateValue"
      @onExecCommand="updateValue"
      @onBlur="updateValue"
      @onPaste="updateValue"
      @onUndo="updateValue"
      @onRedo="updateValue"
    />
  </div>
</template>

<script>
import mixin from "@directus/extension-toolkit/mixins/interface";

import "tinymce/tinymce";
import "tinymce/themes/silver";
import "tinymce/plugins/media/plugin";
import "tinymce/plugins/table/plugin";
import "tinymce/plugins/hr/plugin";
import "tinymce/plugins/lists/plugin";
import "tinymce/plugins/link/plugin";
import "tinymce/plugins/image/plugin";
import "tinymce/plugins/print/plugin";
import "tinymce/plugins/pagebreak/plugin";
import "tinymce/plugins/code/plugin";
import "tinymce/plugins/insertdatetime/plugin";
import "tinymce/plugins/autoresize/plugin";
import "tinymce/plugins/paste/plugin";
import "tinymce/plugins/preview/plugin";

import Editor from "@tinymce/tinymce-vue";

export default {
  components: {
    Editor
  },
  mixins: [mixin],
  computed: {
    initOptions() {
      return {
        skin: false,
        skin_url: false,
        content_css: false,

        plugins:
          "media table hr lists link image print pagebreak code insertdatetime autoresize paste preview",
        branding: false,
        max_height: 1000,
        elementpath: false,
        statusbar: false,
        menubar: false,
        convert_urls: false,
        readonly: this.readonly,
        extended_valid_elements: "audio[loop],source",
        toolbar:
          "styleselect bold italic underline table undo redo superscript bullist numlist link unlink image code media removeformat format-1 format-1-red format-1-yellow format-1-green format-2 format-3 details"
      };
    }
  },
  created() {
    this.updateValue = _.debounce(this.updateValue, 200);
  },
  methods: {
    updateValue() {
      const editor = this.$refs.editorElement.editor;
      const newValue = editor.getContent();
      this.$emit("input", newValue);
    }
  }
};
</script>

<style lang="scss" scoped>
@import "~tinymce/skins/ui/oxide/skin.css";
@import "~tinymce/skins/ui/oxide/content.css";
@import "~tinymce/skins/content/default/content.css";
</style>
