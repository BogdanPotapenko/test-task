<template>
  <div class="hero">
    <div class="hero-content">
      <div class="title-area">
        <div class="title-area-logo">
          <img
            width="100%"
            height="100%"
            src="../../assets/icons/logo.svg"
            alt=""
          />
        </div>
        <h1 class="title-area-title">
          Deposit 500, get 500 USDT
          <span> as a gift</span>
        </h1>
        <h2 class="title-area-subtitle">100% cashback for VIPs only</h2>
      </div>
      <my-button
        class="btn"
        @click="isPopup = true"
        value="Become a vip-player"
      ></my-button>
      <popup @close="isPopup = false" :is-popup="isPopup"
        ><registration />
      </popup>
      <div class="brilliant"></div>
      <div class="diamond"></div>
      <div class="light1"></div>
      <div class="light2"></div>
    </div>

    <div class="hero-banner">
      <div class="image2"></div>
      <div class="image3"></div>
      <div class="image4"></div>
      <div class="image5"></div>
      <div class="chip_3d"></div>
    </div>
  </div>
</template>

<script setup>
import { ref, watch } from "vue";

import MyButton from "../ui/MyButton.vue";
import Popup from "../ui/Popup.vue";
import Registration from "../popups/Registration.vue";

const isPopup = ref(false);

watch(isPopup, () => {
  if (isPopup.value) {
    document.body.style.overflow = "hidden";
  } else {
    document.body.style.overflow = "auto";
  }
});
</script>

<style lang="scss" scoped>
.hero {
  width: 100%;
  height: 100vh;
  min-height: 800px;
  display: grid;
  @media (min-width: 1025px) {
    grid-template-columns: 50% 50%;
  }
  @media (max-width: 1024px) {
    grid-template-rows: 50% 50%;
  }

  @media (max-width: 640px) {
    min-height: 700px;
  }
  @media (max-width: 400px) {
    min-height: 650px;
  }

  &-content {
    position: relative;
    display: flex;
    flex-direction: column;
    align-items: flex-start;
    gap: 101px;
    margin: 0 auto;
    z-index: 1;
    padding: 148px 75px 0 60px;

    @media (max-width: 1024px) {
      align-items: center;
      padding: 30px;
      gap: 48px;
      overflow: hidden;
    }
    @media (max-width: 640px) {
      justify-content: start;

      padding: 56px 16px;
    }

    .title-area {
      display: flex;
      flex-direction: column;
      align-items: flex-start;
      gap: 54px;

      @media (max-width: 1024px) {
        align-items: center;
        text-align: center;
        gap: 30px;
      }
      @media (max-width: 640px) {
        gap: 24px;
      }
      &-logo {
        display: block;
        width: calc(141px + (235 - 141) * ((100vw - 375px) / (1920 - 375)));
        height: calc(21px + (35 - 21) * ((100vw - 375px) / (1920 - 375)));
        @media (max-width: 640px) {
          margin-bottom: 16px;
        }
      }
      &-title {
        max-width: calc(300px + (500 - 300) * ((100vw - 375px) / (1920 - 375)));
        color: $white;
        text-transform: uppercase;

        span {
          color: $gold;
          font-weight: 700;
        }
      }
      &-subtitle {
        color: $gray100;
        text-transform: uppercase;
      }
    }
    button {
      position: relative;
      z-index: 2;
    }
    .brilliant {
      width: calc(70px + (165 - 70) * ((100vw - 375px) / (1920 - 375)));
      height: calc(70px + (165 - 70) * ((100vw - 375px) / (1920 - 375)));
      position: absolute;
      bottom: 4%;
      right: 9%;
      transform: rotate(70deg);
      background-image: url(../../assets/img/Brilliant_3D.png);
      background-size: cover;
      background-repeat: no-repeat;
      @media (max-width: 1024px) {
        right: 0%;
        bottom: 2%;
      }
    }
    .diamond {
      width: calc(115px + (320 - 115) * ((100vw - 375px) / (1920 - 375)));
      height: calc(100px + (270 - 100) * ((100vw - 375px) / (1920 - 375)));
      position: absolute;
      top: 31%;
      left: -46%;
      transform: rotate(-42deg);
      background-image: url(../../assets/img/Diamond_2.png);
      background-size: cover;
      background-repeat: no-repeat;
      @media (max-width: 1700px) {
        left: -30%;
      }
      @media (max-width: 1300px) {
        top: 74%;
        left: -7%;
      }
    }
    .light1 {
      width: calc(74px + (212 - 74) * ((100vw - 375px) / (1920 - 375)));
      height: calc(45px + (127 - 45) * ((100vw - 375px) / (1920 - 375)));
      position: absolute;
      top: 11%;
      right: -17%;
      transform: rotate(-21.748deg);
      background-image: url(../../assets/img/Light.png);
      background-size: cover;
      background-repeat: no-repeat;

      @media (max-width: 1024px) {
        right: -6%;
      }
    }
    .light2 {
      width: calc(84px + (237 - 84) * ((100vw - 375px) / (1920 - 375)));
      height: calc(50px + (142 - 50) * ((100vw - 375px) / (1920 - 375)));
      position: absolute;
      bottom: 11%;
      right: -9%;
      background-image: url(../../assets/img/Light.png);
      background-size: cover;
      background-repeat: no-repeat;
      @media (max-width: 1024px) {
        bottom: 15%;
        right: -6%;
      }
    }
  }
  &-banner {
    position: relative;
    background-image: url(../../assets/img/image1.png);
    background-size: cover;
    @media (max-width: 1024px) {
      overflow: hidden;
    }
    .image2 {
      width: calc(113px + (217 - 113) * ((100vw - 375px) / (1920 - 375)));
      height: calc(56px + (111 - 56) * ((100vw - 375px) / (1920 - 375)));
      position: absolute;
      top: 12%;
      left: 50%;
      transform: translate(-50%, 0);
      background-image: url(../../assets/img/image2.png);
      background-size: cover;
      @media (max-width: 1024px) {
        top: 10%;
      }
    }
    .image3 {
      width: calc(117px + (490 - 117) * ((100vw - 375px) / (1920 - 375)));
      height: calc(130px + (550 - 130) * ((100vw - 375px) / (1920 - 375)));
      position: absolute;
      top: 0%;
      right: 0;
      background-image: url(../../assets/img/image3.png);
      background-size: cover;
      @media (max-width: 1024px) {
        top: 16%;
      }
    }
    .image4 {
      width: calc(84px + (280 - 84) * ((100vw - 375px) / (1920 - 375)));
      height: calc(74px + (220 - 74) * ((100vw - 375px) / (1920 - 375)));
      position: absolute;
      top: 43%;
      left: -18%;
      background-image: url(../../assets/img/image4.png);
      background-size: cover;
      @media (max-width: 1024px) {
        top: 82%;
        left: -1%;
      }
    }
    .image5 {
      width: calc(273px + (600 - 273) * ((100vw - 375px) / (1920 - 375)));
      height: calc(297px + (635 - 297) * ((100vw - 375px) / (1920 - 375)));
      position: absolute;
      bottom: 0%;
      left: 10%;
      background-image: url(../../assets/img/image5.png);
      background-size: cover;
      @media (max-width: 1024px) {
        bottom: -20%;
        left: 47%;
        transform: translate(-53%, 0);
      }
      @media (max-width: 640px) {
        bottom: 0%;
        left: 47%;
        transform: translate(-53%, 0);
      }
    }
    .chip_3d {
      width: calc(100px + (350 - 100) * ((100vw - 375px) / (1920 - 375)));
      height: calc(91px + (290 - 91) * ((100vw - 375px) / (1920 - 375)));
      position: absolute;
      top: 0%;
      left: -11%;
      background-image: url(../../assets/img/Chip_3D.png);
      background-size: cover;
      background-repeat: no-repeat;
      @media (max-width: 1024px) {
        transform: rotate(-90deg);
        top: 15%;
        left: -6%;
      }
    }
  }
}
</style>
