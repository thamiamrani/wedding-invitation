<template>
  <div class="invitation">
    <invitation :canOpen="canOpen" @onClose="canOpen = true, hasClosed = true" @sendBarrage="onAfterSending"/>
  </div>
</template>

<script>
  import 'prismjs/themes/prism-okaidia.css'
  import '../utils/raf'
  import Invitation from './Invitation'

  export default {
    name: 'Editor',
    components: { Invitation },
    data() {
      return {
        canOpen: true,
        hasClosed: false,
        canStart: false
      }
    },
    methods: {
      onAfterSending() {
        this.canOpen = false
        setTimeout(() => {
          this.canStart = true
        }, 1200)
      }
    }
  }
</script>

<style lang="less">
  .invitation {
    display: flex;
    justify-content: center;
  }
</style>