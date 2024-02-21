<template>
  <div class="wedding-invitation" :class="{ 'invitation-bounce': canOpen }">
    <div class="invitation-container" :class="{ 'invitation-down': isOpening }">
      <div class="invitation-cover">
        <div class="cover-content" :class="{ 'invitation-up': isOpening }">
          <div class="content-inside">
            <img class="content-inside-photo" src="../images/invite1.png">
          </div>
        </div>
        <div class="cover-inside-left" :class="{ 'opening': isOpening }"></div>
        <div class="cover-inside-right" :class="{ 'opening': isOpening }"></div>
        <img class="cover-inside-seal" src="../images/seal1.png" @click="openInvitation"
          :class="{ 'invitation-flight': isOpening }">
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
  }
}
</script>

<style lang="less">
.wedding-invitation {
  position: fixed;
  width: 100%;
  height: 120%;
  padding-top: 60px;
  padding-bottom: 400px;
  z-index: 4;
  opacity: 0;
  transition: transform 2.8s cubic-bezier(.26, 1.84, .39, .61), opacity 0.5s linear;
  background-size: 100%;
  overflow: hidden;

  &.invitation-bounce {
    opacity: 1;
  }

  .invitation-container {
    display: flex;
    justify-content: center !important;
    align-items: center !important;
    margin-top: 40px;
    transition: transform 2.6s cubic-bezier(0.4, 0, 1, 1);

    &.invitation-down {
      transform: translateY(50px);
    }

    .invitation-cover {
      display: flex !important;
      justify-content: center !important;
      align-items: center !important;
      width: 35%;
      height: 85%;
      border-radius: 5px;
      background-color: #fffded;
      perspective: 500px;
      box-shadow: 0 0 20px 2px rgba(0, 0, 0, 0.15);

      .cover-content {
        height: 80%;
        width: 120%;
        z-index: 9;
        opacity: 0;
        padding: 10px 20px;
        transition: transform 2.2s cubic-bezier(0.4, 0, 1, 1);
        overflow: hidden;

        &.invitation-up {
          transform: translateY(-60px);
          transform: scale(1.48);
          animation: coverhide 1.8s forwards;
        }

        @keyframes coverhide {
          0% {
            opacity: 0;
          }

          99.999% {
            opacity: 0.99;
          }

          100% {
            opacity: 1;
            margin-top: 50px;
          }
        }

        .content-inside {
          height: 100%;
          padding: 6px;
          color: #a9895d;
          background-color: #3c4d45;
          text-align: center;
          overflow: hidden;
          scrollbar-width: none;

          .content-inside-photo {
            width: 100%;
            padding: 6px;
            border: 0.5px solid #ebf3d0c7;
          }

          p {
            margin-top: 0;
            margin-bottom: 5px;
          }
        }
      }

      .cover-inside-left {
        position: absolute;
        left: 0;
        top: 0;
        width: 70%;
        height: 120%;
        border-radius: 10px;
        background-color: #f9f7e7;
        box-shadow: 5px 0 10px rgba(0, 0, 0, 0.2);
        z-index: 6;
        transition: transform 2s;
        transform-origin: 0 50%;

        &.opening {
          transform: rotate3d(0, 1, 0, -140deg);
        }
      }

      .cover-inside-right {
        position: absolute;
        right: 0;
        top: 0;
        width: 40%;
        height: 120%;
        border-radius: 10px;
        background-color: #385447;
        box-shadow: -5px 0 10px rgba(0, 0, 0, 0.2);
        z-index: 5;
        transition: transform 1.7s;
        transform-origin: 100% 50%;

        &.opening {
          transform: rotate3d(0, 1, 0, 140deg);
        }
      }

      .cover-inside-seal {
        position: absolute;
        top: 80%;
        left: 70%;
        bottom: 100px;
        max-width: 100px;
        max-height: 100px;
        margin-left: -40px;
        z-index: 10;
        transform-origin: 50% 50%;
        transition: all 1.4s cubic-bezier(0.4, 0, 1, 1);
        animation: pulse 3s linear infinite;

        &.invitation-flight {
          opacity: 0;
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
      }
    }
  }

  @media only screen and (max-width: 1050px) {

    .cover-content {
      display: flex !important;
      align-items: center !important;
      justify-content: center !important;

      &.invitation-up {
        height: 105% !important;
      }
    }

    .invitation-container {
      display: flex !important;
      align-items: center !important;
      justify-content: center !important;
      height: 110%;
    }

    .invitation-cover {
      display: flex !important;
      width: 75% !important;
      height: 83% !important;
    }

    &.invitation-up {
      transform: translateY(-190px);
      animation: coverhide 1.8s forwards;
    }

    .content-inside {
      display: flex;
      justify-content: center;
      align-content: center;
      width: 85%;
      height: 88% !important;
    }
  }
}
</style>
