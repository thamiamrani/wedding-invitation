<template>
  <div class="invitation-page invitation-t">
    <div class="invitation-card" :class="{ 'opening': isOpening }">
      <img id="frame" src="../images/invite.png">
      <div class="card-content image">
        <img :class="{ 'opening': isOpening }" src="../images/invite.png">
      </div>
      <div class="card-content cover">
        <div class="rsvp" @click="rsvp" :class="{ 'opening': isOpening }">
        </div>
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
      if (this.isOpening === false) {
        this.isOpening = true
      }
    },
    rsvp() {
      window.location.href = "https://www.theknot.com/us/maria-dinu-and-thami-amrani-aug-2024/rsvp"
    }
  },
  beforeMount() {
    setTimeout(() => this.openInvitation(), 5000);

  }
}
</script>

<style lang="less">
.invitation-page {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  flex-grow: 1;
  max-height: 100%;
}

.rsvp {
  margin-bottom: 0.2rem;
  position: absolute;
  width: 40%;
  aspect-ratio: 1;
  top: 6%;
  left: 39%;
  z-index: 3;
  background-image: url("../images/RSVP.png");
  background-size: contain;
  background-repeat: no-repeat;
  opacity: 0;
  &.opening {
    animation: appear-rsvp 3s linear forwards, pulse-rsvp 3s linear infinite;
    animation-delay: 6s;
  }
}

.invitation-card {
  position: relative;
  max-height: 100%;

  #frame {
    opacity: 0;
    max-height: 90%;
  }

  .card-content {
    position: absolute;
    background-color: white;
    border-radius: 0.5rem;
    width: 100%;
    height: 100%;
    top: 0;
    left: 0;
    display: flex;
    justify-content: center;

    & > img {
      max-height: 100%;
      &.opening {
        z-index: 2;
        animation: appear 3s linear forwards;
      }
    }
  }

  .cover {
    display: flex;

    .left-pane {
      background: #faefdd;
      flex-grow: 2;
      border-radius: 0.5rem;
      transition: all 1.5s cubic-bezier(0.4, 0, 1, 1);
      transform-origin: 0 50%;
  
      &.opening {
        transform: rotate3d(0, 1, 0, -140deg);
        flex-grow: 1;
      }
    }

    .right-pane {
      background: rgba(232, 231, 231, 0.926);
      border-radius: 0.5rem;
      flex-grow: 1;
      transition: all 1.5s cubic-bezier(0.4, 0, 1, 1);
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
    animation: pulse 2.8s linear infinite;


    &.opening {
      opacity: 0;
    }
  }

  @keyframes appear {
    0% {
      opacity: 0;
      transform: scale(1.00);
    }

    50% {
      transform: scale(1.0999);
    }

    99.999% {
      opacity: 0.99999;
      transform: scale(1.209999);
    }

    100% {
      opacity: 1;
      transform: scale(1.21);
    }
  }
  @keyframes appear-rsvp {
    0% {
      opacity: 0;
      transform: scale(1.00);
    }

    50% {
      opacity: 0.5;
      transform: scale(1.6);
    }

    99.999% {
      opacity: 0.99999;
      transform: scale(2.19999);
    }

    100% {
      opacity: 1;
      transform: scale(2.2);
    }
  }

  @keyframes pulse {
    0% {
      transform: scale(1.05);
    }

    50% {
      transform: scale(0.9);
    }

    100% {
      transform: scale(1.05);
    }
  }

  @keyframes pulse-rsvp {
    0% {
      transform: scale(2.2);
    }

    50% {
      transform: scale(2.1);
    }

    100% {
      transform: scale(2.2);
    }
  }

}
}
</style>
