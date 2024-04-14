<template>
  <div class="wedding">
    <Editor />
  </div>
</template>

<script>
import Editor from "./components/Editor.vue"

export default {
  props: [],
  components: {
    Editor
  },
  name: 'Wedding'
}

</script>

<style lang="less">
@import './assets/base.less';

html,
body {
  width: 100%;
  height: 100vh;
}

.wedding {
  width: 100%;
  height: 100%;
  display: flex;
  justify-content: center;
  padding: 2rem 2rem 6rem 2rem;
}
</style>
