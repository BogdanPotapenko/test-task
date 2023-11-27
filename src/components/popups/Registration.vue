<template>
  <div class="registration">
    <div class="registration-banner">
      <div class="registration-banner-logo">
        <img src="../../assets/icons/logo.svg" alt="" />
      </div>
      <div class="registration-banner-text">
        <h3>Deposit 500, <br />get 500 USDT as a gift</h3>
        <h3 class="gold">100% cashback for VIPs only</h3>
      </div>
      <div class="image1"></div>
      <div class="image2"></div>
      <div class="image3"></div>
      <div class="image4"></div>
      <div class="ellipse1"></div>
      <div class="ellipse2"></div>
      <div class="ellipse3"></div>
      <div class="ellipse4"></div>
      <div class="ellipse5"></div>
    </div>
    <div class="registration-area">
      <h4 class="registration-area-title">Registration</h4>
      <form @submit.prevent="onSubmit" class="registration-form" action="">
        <my-input
          v-model="email"
          label="Email"
          type="text"
          icon="email.svg"
          :error="erroreEmail"
        ></my-input>
        <my-input
          v-model="password"
          label="Password"
          type="password"
          icon="password.svg"
          :error="errorPassword"
        ></my-input>
        <div class="checkboox-area">
          <my-checkbox
            v-model="checkbox"
            @update="checkbox = !checkbox"
          ></my-checkbox>
          <p>
            By checking this box when registering on this site, the user
            confirms that he is over 18 years of age and has read, understood
            and accepted the <a href="#"> Terms and Conditions.</a>
          </p>
        </div>
        <my-button-square
          class="registration-button"
          value="Create an account"
          :disabled="!isValid"
        />
      </form>
      <div class="sign-up">
        <h5 class="sign-up-title">Or register with:</h5>
        <div class="sign-up-soocials">
          <button><img src="../../assets/icons/metamask.svg" alt="" /></button>
          <button><img src="../../assets/icons/apple.svg" alt="" /></button>
          <button><img src="../../assets/icons/facebook.svg" alt="" /></button>
          <button><img src="../../assets/icons/google.svg" alt="" /></button>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { computed } from "vue";

import { useField, useForm } from "vee-validate";
import * as yup from "yup";

import MyButtonSquare from "../ui/MyButtonSquare.vue";
import MyInput from "../ui/MyInput.vue";
import MyCheckbox from "../ui/MyCheckbox.vue";

const emailValidator =
  /^(?:[a-z0-9!#$%&'*+/=?^_`{|}~-]+(?:\.[a-z0-9!#$%&'*+/=?^_`{|}~-]+)*|"(?:[\x01-\x08\x0b\x0c\x0e-\x1f\x21\x23-\x5b\x5d-\x7f]|\\[\x01-\x09\x0b\x0c\x0e-\x7f])*")@(?:(?:[a-z0-9](?:[a-z0-9-]*[a-z0-9])?\.)+[a-z0-9](?:[a-z0-9-]*[a-z0-9])?|\[(?:(?:25[0-5]|2[0-4][0-9]|[01]?[0-9][0-9]?)\.){3}(?:25[0-5]|2[0-4][0-9]|[01]?[0-9][0-9]?|[a-z0-9-]*[a-z0-9]:(?:[\x01-\x08\x0b\x0c\x0e-\x1f\x21-\x5a\x53-\x7f]|\\[\x01-\x09\x0b\x0c\x0e-\x7f])+)\])$/;

const validationSchema = yup.object({
  email: yup
    .string()
    .matches(emailValidator, "Provide a valid e-mail address")
    .required("Provide a valid e-mail address"),
  password: yup
    .string()
    .required("Password must be at least 6 characters")
    .min(6, "Password must be at least 6 characters"),
});

const { handleSubmit } = useForm({
  validationSchema,
  initialValues: {
    password: "",
    email: "",
    checkbox: false,
  },
});

const { value: password, errorMessage: errorPassword } = useField("password");
const { value: email, errorMessage: erroreEmail } = useField("email");
const { value: checkbox } = useField("checkbox");

const isValid = computed(() => email.value && password.value && checkbox.value);

const onSubmit = async (values) => {
  const formData = {};

  formData.email = email.value;
  formData.password = password.value;
  try {
    await console.log(formData);
    email.value = "";
    password.value = "";
    checkbox.value = false;
  } catch (e) {
    console.log(e);
  }
};
</script>

<style lang="scss" scoped>
.registration {
  width: 100%;
  height: 100%;
  display: grid;
  @media (min-width: 1025px) {
    grid-template-columns: 50% 50%;
  }
  @media (max-width: 1024px) {
    grid-template-rows: 37% 63%;
  }
  &-banner {
    position: relative;
    overflow: hidden;
    display: flex;
    flex-direction: column;
    align-items: center;
    padding: 56px 24px;
    gap: 47px;
    flex: 1 0 0;
    align-self: stretch;
    background: $purple;
    @media (max-width: 1024px) {
      padding: 54px 3px;
      gap: 24px;
    }
    &-logo,
    &-text {
      position: relative;
      z-index: 11;
    }
    &-logo {
      display: block;
      width: calc(135px + (141 - 135) * ((100vw - 375px) / (1920 - 375)));
      height: calc(20px + (21 - 20) * ((100vw - 375px) / (1920 - 375)));
      img {
        width: 100%;
        height: 100%;
      }
    }
    &-text {
      display: flex;
      max-width: 312px;
      flex-direction: column;
      align-items: center;
      gap: 8px;
      color: $main;
      text-align: center;
      text-transform: uppercase;
      .gold {
        color: $lightgold;
      }
    }
    .image1 {
      width: 90px;
      height: 120px;
      position: absolute;
      top: 33%;
      right: 0;
      background-image: url(../../assets/img/image3.png);
      background-size: cover;
      @media (max-width: 1024px) {
        top: 57%;
      }
    }
    .image2 {
      width: 75px;
      height: 75px;
      position: absolute;
      top: 43%;
      left: 4%;
      background-image: url(../../assets/img/image4.png);
      background-size: cover;
      @media (max-width: 1024px) {
        top: 52%;
        left: -8%;
      }
    }
    .image3 {
      width: 110px;
      height: 110px;
      position: absolute;
      bottom: -6%;
      left: 1%;
      transform: rotate(-80deg);
      background-image: url(../../assets/img/image4.png);
      background-size: cover;
      @media (max-width: 1024px) {
        bottom: -22%;
        left: -2%;
      }
    }
    .image4 {
      width: calc(164px + (360 - 164) * ((100vw - 375px) / (1920 - 375)));
      height: calc(149px + (400 - 149) * ((100vw - 375px) / (1920 - 375)));
      position: absolute;
      bottom: 0;
      left: 2%;
      background-image: url(../../assets/img/image5.png);
      background-size: cover;
      @media (max-width: 1024px) {
        top: 50%;
        left: 48%;
        transform: translate(-52%, 0);
      }
      @media (max-width: 500px) {
        top: auto;
        bottom: 0;
      }
    }
    .ellipse1 {
      width: 100%;
      height: 400px;
      position: absolute;
      bottom: -4%;
      left: 50%;
      transform: translate(-50%, 0);

      background-image: url(../../assets/icons/ellipse1.svg);
      background-size: cover;
      @media (max-width: 1024px) {
        bottom: -60%;
      }
    }
    .ellipse2 {
      width: calc(100px + (300 - 100) * ((100vw - 375px) / (1920 - 375)));
      height: calc(100px + (300 - 100) * ((100vw - 375px) / (1920 - 375)));
      position: absolute;
      top: 35%;
      left: 0%;

      background-image: url(../../assets/icons/ellipse2.svg);
      background-size: contain;
      background-repeat: no-repeat;
    }
    .ellipse3 {
      width: calc(100px + (300 - 100) * ((100vw - 375px) / (1920 - 375)));
      height: calc(100px + (300 - 100) * ((100vw - 375px) / (1920 - 375)));
      position: absolute;
      bottom: 10%;
      right: -35%;

      background-image: url(../../assets/icons/ellipse3.svg);
      background-size: contain;
      background-repeat: no-repeat;
    }
    .ellipse4 {
      width: calc(100px + (300 - 100) * ((100vw - 375px) / (1920 - 375)));
      height: calc(100px + (300 - 100) * ((100vw - 375px) / (1920 - 375)));
      position: absolute;
      bottom: -7%;
      left: -2%;

      background-image: url(../../assets/icons/ellipse4.svg);
      background-size: contain;
      background-repeat: no-repeat;
      @media (max-width: 1024px) {
        bottom: -20%;
      }
    }
    .ellipse5 {
      width: calc(100px + (300 - 100) * ((100vw - 375px) / (1920 - 375)));
      height: calc(100px + (300 - 100) * ((100vw - 375px) / (1920 - 375)));
      position: absolute;
      top: 30%;
      right: -20%;
      background-image: url(../../assets/icons/ellipse5.svg);
      background-size: contain;
      background-repeat: no-repeat;
    }
  }
  &-area {
    display: flex;
    padding: 16px;
    margin-top: 72px;
    flex-direction: column;
    align-items: center;
    gap: 32px;
    flex: 1 0 0;
    align-self: stretch;
    background: $gray900;
    @media (max-width: 1024px) {
      margin-top: 0;
    }
    &-title {
      color: $main;
      text-align: center;
      padding: 16px;
      @media (max-width: 1024px) {
        padding: 16px 0 8px 0;
      }
    }

    .registration-form {
      max-width: 328px;
      display: flex;
      flex-direction: column;
      align-items: center;
      gap: 24px;

      .checkboox-area {
        display: flex;
        padding: 0px 2px;
        align-items: flex-start;
        gap: 8px;
        align-self: stretch;
        padding: 8px 0;
        @media (max-width: 1024px) {
          padding: 8px 2px 26px 0;
        }
        p {
          color: $gray100;
          a {
            color: $lightgold;
          }
        }
      }
    }
    .sign-up {
      display: flex;
      flex-direction: column;
      align-items: center;
      gap: 12px;
      padding-bottom: 16px;
      align-self: stretch;
      &-title {
        color: $main;
        text-align: center;
      }
      &-soocials {
        display: flex;
        justify-content: center;
        align-items: flex-start;
        gap: 8px;
        align-self: stretch;
        button {
          display: flex;
          padding: 8px;
          justify-content: center;
          align-items: center;
          gap: 8px;
          border-radius: 8px;
          background: $gray400;
          &:hover {
            border: 1px solid $gray100;
          }
        }
      }
    }
  }
}
</style>
