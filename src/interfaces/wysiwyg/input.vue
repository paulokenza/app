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
    <v-item-select
      v-if="selectExisting"
      collection="directus_files"
      :fields="['title', 'filename']"
      :filters="[]"
      single
      :value="selectedFile"
      @input="selectedFile = $event"
      @done="selectCallback"
      @cancel="() => {}"
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
import "tinymce/plugins/image/plugin";
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
  data() {
    return {
      selectExisting: false,
      selectedFile: null,
      selectCallback: () => {}
    };
  },
  computed: {
    initOptions() {
      const styleFormats = this.getStyleFormats();
      let toolbarString = this.options.toolbar.join(" ");

      if (styleFormats) {
        toolbarString += " styleselect";
      }

      return {
        skin: false,
        skin_url: false,
        content_css: false,
        content_style: this.contentStyle,
        plugins:
          "media table hr lists image link pagebreak code insertdatetime autoresize paste preview",
        branding: false,
        max_height: 1000,
        elementpath: false,
        statusbar: false,
        menubar: false,
        convert_urls: false,
        readonly: this.readonly,
        extended_valid_elements: "audio[loop],source",
        toolbar: toolbarString,
        style_formats: styleFormats,
        file_picker_callback: this.selectFile
      };
    },
    contentStyle() {
      return `
        h1 {
          font-size: 12px;
        }
      `;
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
      if (Array.isArray(this.options.custom_formats) && this.options.custom_formats.length > 0) {
        return this.options.custom_formats;
      }

      return null;
    },
    selectFile(callback) {
      this.selectExisting = true;
      this.selectCallback = async () => {
        const { data: file } = await this.$api.getItem("directus_files", this.selectedFile);
        this.selectExisting = false;
        // TODO: Make sure it returns the correct keys for non-image type files. See
        // https://www.tiny.cloud/docs/configure/file-image-upload/#example for an example
        callback(file.data.full_url, { alt: file.title });
      };
    }
  }
};
</script>

<style lang="scss" scoped>
@import "~tinymce/skins/ui/oxide/skin.css";
@import "~tinymce/skins/ui/oxide/content.css";
@import "~tinymce/skins/content/default/content.css";
@import "./tinymce-overrides.css";
</style>
