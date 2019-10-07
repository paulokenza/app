<template>
  <div>
    <ProjectSwitcher :selected-project="0" />
  </div>
</template>

<script>
import ProjectSwitcher from "../components/login/project-switcher";
export default {
  name: "Login",
  components: { ProjectSwitcher }
};
</script>

<style lang="scss"></style>
