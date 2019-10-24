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
        icons: "material",

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

<style lang="scss">
@import "~tinymce/skins/ui/oxide/skin.css";
@import "~tinymce/skins/ui/oxide/content.css";
@import "~tinymce/skins/content/default/content.css";

// Editor Chrome

.tox-tinymce {
  border: var(--input-border-width) solid var(--lighter-gray);
  border-radius: var(--border-radius);
  color: var(--gray);
  transition: var(--fast) var(--transition);
  transition-property: color, border-color;
}

.tox .tox-toolbar,
.tox .tox-toolbar__primary,
.tox .tox-toolbar__overflow {
  background: url("data:image/svg+xml;charset=utf8,%3Csvg height='39px' viewBox='0 0 40 39px' width='40' xmlns='http://www.w3.org/2000/svg'%3E%3Crect x='0' y='37px' width='100' height='2' fill='%23b0bec5'/%3E%3C/svg%3E")
    left 0 top 0 #fff;
}

.tox .tox-tbtn--enabled,
.tox .tox-tbtn--enabled:hover,
.tox .tox-tbtn:hover {
  background: var(--blue-grey-100);
  color: var(--darkest-gray);
}

.tox .tox-tbtn {
  margin-right: 2px;
}

.tox .tox-tbtn svg {
  fill: var(--darker-gray);
}

.mce-content-body {
  margin: 20px;
}

// Modal

.tox .tox-dialog-wrap__backdrop {
  background-color: rgba(0, 0, 0, 0.75);
}

.tox .tox-dialog {
  border: none;
  box-shadow: none;
}

.tox .tox-dialog--width-lg {
  max-width: 800px;
}

.tox .tox-dialog__header {
  padding: 16px 24px 0 24px;
}

.tox .tox-dialog__body-content {
  padding: 24px 24px;
}

.tox .tox-dialog__footer {
  padding: 0 24px 24px;
}

.tox .tox-textfield,
.tox .tox-toolbar-textfield,
.tox .tox-selectfield select,
.tox .tox-textarea {
  border: var(--input-border-width) solid var(--lighter-gray);
  border-radius: var(--border-radius);
  color: var(--gray);
  transition: var(--fast) var(--transition);
  font-family: monospace;
  padding: 12px;
}

.tox .tox-textfield:focus,
.tox .tox-selectfield select:focus,
.tox .tox-textarea:focus {
  border-color: var(--lighter-gray);
}

.tox .tox-dialog__footer {
  border-top: none;
}

.tox .tox-button {
  background-color: var(--darker-gray);
  border-color: var(--darker-gray);
  border: none;
  border-radius: var(--border-radius);
  cursor: pointer;
  -webkit-transition: var(--fast) var(--transition);
  transition: var(--fast) var(--transition);
  transition-property: border-color, background-color, color;
  display: flex;
  align-items: center;
  justify-content: center;
  padding: 0 20px 1px;
  height: 44px;
  min-width: 136px;
  border: var(--input-border-width) solid var(--action);
  color: var(--white);
  font-size: 16px;
  line-height: 19px;
  font-weight: 500;
}

.tox .tox-button:hover:not(:disabled) {
  background-color: var(--darkest-gray);
  border-color: var(--darkest-gray);
}

.tox .tox-button--secondary {
  background-color: var(--lighter-gray);
  border-color: var(--lighter-gray);
}

.tox .tox-button--secondary:hover:not(:disabled) {
  background-color: var(--light-gray);
  border-color: var(--light-gray);
}

.tox .tox-button--naked {
  background-color: transparent;
  border-color: transparent;
  color: var(--darker-gray);
  min-width: auto;
  height: auto;
}

.tox .tox-button--naked.tox-button--icon:hover:not(:disabled) {
  background-color: transparent;
  border-color: transparent;
  color: var(--darker-gray);
}

.tox .tox-form__group {
  margin-top: 24px;
}

.tox .tox-label,
.tox .tox-toolbar-label {
  font-size: var(--size-2);
  margin-bottom: 10px;
  color: var(--darkest-gray);
}
</style>
