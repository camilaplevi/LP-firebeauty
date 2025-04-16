<script lang="ts">
import { ref, defineComponent } from 'vue';

export default defineComponent({
  setup() {
    const titleText = ref('A beleza\ndo agora!')
    const subTitleText = ref('Encontre os melhores profissionais de estética,\nagende com um toque, e compartilhe sua\nessência com o mundo.')

    const nome = ref('')
    const whatsapp = ref('')

    return {
      titleText,
      subTitleText,
      nome,
      whatsapp
    }
  }
})

</script>

<template>
  <q-layout view="lHh Lpr lFf">
    <q-header elevated class="bg-white" style="height: 70px;">
      <div class="row justify-center items-center" style="height: 100%;">
        <img src="/src/assets/Logo horizontal preta 4.png" alt="Logo FireBeauty"
          style="width: 141px !important; height: 49px !important; margin: 0 0 10px 0;">
      </div>
    </q-header>
    <q-page-container>
      <q-page class="no-padding">
        <div class="hero-section relative-position" style="height: 100vh;">
          <img src="/src/assets/Rectangle 3.png" alt="Background" style="width: 100%; object-fit: cover;">
        </div>
        <div class="absolute-left text-left text-white" style="width: 80%; max-width: 600px;">
          <h1 class="text-h4"
            style="font-family: 'IvyMode'; font-size: 30px; font-size: 70px; margin: 0; padding: 40px 0 40px 100px; line-height: 60px; white-space: pre-line;">
            {{ titleText }}
          </h1>
          <p class="text-subtitle1"
            style="font-family: 'Poppins'; margin-left: 100px; white-space: pre-line; font-weight: 400; line-height: 26px;">
            {{ subTitleText }}
          </p>
          <q-card class="q-pa-md" style="background-color: #D9D9D9; border-radius: 18px; margin: 60px 0 0 100px; ">
            <q-input filled v-model="nome" label="Seu nome:" class="q-mb-md"
              style="background-color: #F5F5F5; border-radius: 8px; border: 1px solid var(--Bege-luxuoso, #AD9B8E);" />
            <q-input filled v-model="whatsapp" label="Seu WhatsApp:" mask="(##) #####-####"
              style="background-color: #F5F5F5; border-radius: 8px; border: 1px solid var(--Bege-luxuoso, #AD9B8E);" />
            <q-btn label="Enviar" class="q-mt-md full-width"
              style="background-color: #FFA600; color: #322D29; height: 45px; border-radius: 32.5px;" />
          </q-card>
        </div>

      </q-page>
    </q-page-container>
  </q-layout>
</template>