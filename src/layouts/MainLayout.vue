<script lang="ts">
import { defineComponent, ref } from 'vue';
import { imagesContainer } from 'src/assets/images/Images'

export default defineComponent({
  setup() {
    const textPrivacy = ref('Política de privacidade')
    const textDireitos = ref('Todos os direitos reservados por FireBeauty')

    return {
      imagesContainer,
      textPrivacy,
      textDireitos
    }
  }
})


</script>

<template>
  <q-layout view="hhh Lpr lFf">
    <q-header elevated class="bg-white header">
      <div class="header-content">
        <img :src="imagesContainer.logo" alt="Logo FireBeauty" class="logo"
          style="width: 141px; height: 49px; margin-bottom: 10px;">
      </div>
    </q-header>

    <q-page-container style="padding: 0;">
      <router-view v-slot="{ Component }">
        <keep-alive>
          <component :is="Component" />
        </keep-alive>
      </router-view>
    </q-page-container>

    <q-footer class="page-footer" style="position: relative;">
      <div class="footer-content">
        <img :src="imagesContainer.logo" alt="Logo FireBeauty" class="footer-logo">
        <p class="privacy-text">{{ textPrivacy }}</p>
      </div>
      <q-separator color="#D9D9D9" class="footer-separator" />
      <div style="justify-content: center; display: flex;">
        <p class="copyright-text">{{ textDireitos }}</p>
      </div>
    </q-footer>
  </q-layout>
</template>

<style lang="scss" scoped>
.header {
  height: 70px;

  &-content {
    height: 100%;
    display: flex;
    justify-content: center;
    align-items: center;
  }
}

.page-footer {
  background-color: white;
  height: auto;
  padding: 1rem 0;

  .footer-content {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: space-between;
    height: auto;
    padding: 0 1rem;

    @media (min-width: 769px) {
      flex-direction: row;
      height: 80px;
      padding: 0 100px;
    }
  }

  .footer-logo {
    width: 141px;
    height: 49px;
    margin: 0.5rem 0;

    @media (min-width: 769px) {
      margin-left: 100px;
    }
  }

  .privacy-text {
    font-family: 'Poppins';
    font-weight: 500;
    font-size: 1.5rem;
    color: $tertiary;
    margin: 0.5rem 0;

    @media (min-width: 769px) {
      padding-right: 100px;
      font-size: 1rem;
    }
  }

  .footer-separator {
    margin: 0.5rem 0;
  }

  .copyright-text {
    width: 230px;
    font-family: 'Poppins';
    color: $ligth-brown;
    text-align: center;
    padding: 0.5rem 0;

    @media (min-width: 769px) {
      width: auto;
    }
  }
}
</style>