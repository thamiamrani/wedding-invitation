<template>
  <div class="wedding">
    <Editor/>
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
body{
  height: 100%;
}

.wedding{
  position: relative;
  max-width: 100%;
  height: 100%;
  min-height: 100%;
  margin: 0 auto;
  perspective: 500px;
}
</style>
