<template>
  <label v-if="projects" class="project-switcher">
    <select id="selectedProject" name="selectedProject" :value="selectedProject">
      <option
        v-for="({ url, project_name }, index) in projects"
        :key="url"
        :value="index"
        :checked="selectedProject === index"
      >
        {{ project_name }}
      </option>
      <option v-if="allowOther" value="other">{{ $t("other") }}</option>
    </select>
    <div>
      <v-signal :strength="2" class="connection" />
      {{ projects[selectedProject].project_name || $t("choose_project") }}
      <v-icon
        v-if="projects.length > 1 || allowOther"
        size="24"
        class="icon"
        name="arrow_drop_down"
      />
    </div>
  </label>
</template>

<script>
import { mapState } from "vuex";
import VSignal from "../signal";

const allowOther = window.__DirectusConfig__.allowOther;

export default {
  name: "ProjectSwitcher",
  components: {
    VSignal
  },
  props: {
    selectedProject: {
      type: Number,
      required: true
    }
  },
  computed: {
    ...mapState(["projects"]),
    allowOther: () => allowOther
  }
};
</script>

<style lang="scss"></style>
