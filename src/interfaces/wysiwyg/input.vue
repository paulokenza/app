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
import meta from "./meta.json";

import "tinymce/tinymce";
import "tinymce/themes/silver";
import "tinymce/plugins/media/plugin";
import "tinymce/plugins/table/plugin";
import "tinymce/plugins/hr/plugin";
import "tinymce/plugins/lists/plugin";
import "tinymce/plugins/link/plugin";
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

        plugins: "media table hr lists link pagebreak code insertdatetime autoresize paste preview",
        branding: false,
        max_height: 1000,
        elementpath: false,
        statusbar: false,
        menubar: false,
        convert_urls: false,
        readonly: this.readonly,
        extended_valid_elements: "audio[loop],source",
        toolbar: "styleselect " + this.options.toolbar.join(" "),
        style_formats: this.getStyleFormats()
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
    },
    getStyleFormats() {
      const styleFormats = [];

      if (this.options.headings.length > 0) {
        styleFormats.push({
          title: "Headings",
          items: this.options.headings.map(format => ({
            title: meta.options.headings.options.choices[format],
            format: format
          }))
        });
      }

      if (this.options.inline.length > 0) {
        styleFormats.push({
          title: "Inline",
          items: this.options.inline.map(format => ({
            title: meta.options.inline.options.choices[format],
            format: format
          }))
        });
      }

      if (this.options.blocks.length > 0) {
        styleFormats.push({
          title: "Blocks",
          items: this.options.blocks.map(format => ({
            title: meta.options.blocks.options.choices[format],
            format: format
          }))
        });
      }

      if (this.options.alignment.length > 0) {
        styleFormats.push({
          title: "Align",
          items: this.options.alignment.map(format => ({
            title: meta.options.alignment.options.choices[format],
            format: format
          }))
        });
      }

      return styleFormats;
    }
  }
};
</script>

<style lang="scss" scoped>
@import "~tinymce/skins/ui/oxide/skin.css";
@import "~tinymce/skins/ui/oxide/content.css";
@import "~tinymce/skins/content/default/content.css";
</style>
