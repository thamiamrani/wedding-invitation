<template>
  <div class="invitation-page">
    <div class="rsvp">Click me</div>
    <div class="invitation-card" :class="{ 'opening': isOpening }">
      <img id="frame" src="../images/invite1.png">
      <div class="card-content image">
        <img src="../images/invite1.png">
      </div>
      <div class="card-content cover">
        <div class="seal" @click="openInvitation" :class="{ 'opening': isOpening }"></div>
        <div class="left-pane" :class="{ 'opening': isOpening }"></div>
        <div class="right-pane" :class="{ 'opening': isOpening }"></div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: ['canOpen'],
  data() {
    return {
      isOpening: false,
    }
  },
  methods: {
    openInvitation() {
      this.isOpening = true
    },
    rsvp() {
      window.location.href = "https://www.theknot.com/us/maria-dinu-and-thami-amrani-aug-2024/rsvp"
    }
  }
}
</script>

<style lang="less">
.invitation-page {
  display: flex;
  flex-direction: column;
  justify-content: center;
  flex-grow: 1;
}

.rsvp {
  margin-bottom: 1rem;
}

.invitation-card {
  position: relative;

  #frame {
    opacity: 0;
  }

  .card-content {
    position: absolute;
    width: 100%;
    height: 100%;
    top: 0;
    left: 0;
  }

  .cover {
    display: flex;

    .left-pane {
      background: blue;
      flex-grow: 2;
      transition: all 2s;
      transform-origin: 0 50%;
  
      &.opening {
        transform: rotate3d(0, 1, 0, -140deg);
        flex-grow: 1;
      }
    }

    .right-pane {
      background: green;
      flex-grow: 1;
      transition: all 2s;
      transform-origin: 100% 50%;
  
      &.opening {
        transform: rotate3d(0, 1, 0, 140deg);
      }
    }

  .seal {
    position: absolute;
    width: 25%;
    aspect-ratio: 1;
    top: 75%;
    left: calc(66.6% - 25%/2);
    background-image: url("../images/seal1.png");
    background-size: contain;
    background-repeat: no-repeat;
    transition: opacity s;

    &.opening {
      opacity: 0;
    }
  }
  }
}
</style>
