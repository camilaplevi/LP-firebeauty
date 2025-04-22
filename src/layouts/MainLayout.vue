<script lang="ts">
import { ref, defineComponent, computed } from 'vue';
import { cardIcons } from 'src/assets/icons/CardsIcons'

export default defineComponent({
  setup() {
    const titleText = ref('A beleza\ndo agora!')
    const subTitleText = ref('Encontre os melhores profissionais de estética,\nagende com um toque, e compartilhe sua\nessência com o mundo.')
    const textListaVip = ref('Lista exclusiva. Sem spam, só beleza.')
    const textInitPage = ref('Rede Social da Beleza')
    const subTextInitPage = ref(`Criado para quem entende que ${'<strong>tempo</strong>'} \ntambém é ${'<strong>autocuidado</strong>'}.`)
    const textUnderCards = ref('Mais de 1486 pessoas já garantiram sua vaga na lista VIP de download antecipado!')
    const textListaVipSecond = ref('Lista de download VIP')
    const textAccess = ref('Acesso antecipado à versão beta')
    const textDescount = ref('Descontos nas primeiras propagandas dentro do aplicativo')
    const textMemberFounder = ref('Selo de membro fundadora no perfil')
    const textPrivacy = ref('Política de privacidade')
    const textDireitos = ref('Todos os direitos reservados por FireBeauty')

    const cards = ref([
      {
        title: 'Agendamento\nem poucos\ncliques',
        subtitle: 'Tudo em um só lugar, direto com profissionais selecionados.',
        icon: cardIcons.clock
      },
      {
        title: 'Rede social exclusiva de beleza',
        subtitle: 'Inspire-se. Compartilhe. Conecte-se.',
        icon: cardIcons.heart
      },
      {
        title: 'Geolocalização refinada',
        subtitle: 'Descubra talentos ao seu redor — com discrição e precisão.',
        icon: cardIcons.web
      },
      {
        title: 'Portfólios profissionais',
        subtitle: 'Veja o trabalho antes de escolher. Com tranquilidade.',
        icon: cardIcons.star
      }
    ])

    const nome = ref('')
    const whatsapp = ref('')

    const formattedUnderCards = computed(() => {
      return textUnderCards.value.replace(
        '1486 pessoas',
        '<span style="color: #AD9B8E">1486 pessoas</span>'
      );
    });

    return {
      titleText,
      subTitleText,
      nome,
      whatsapp,
      textListaVip,
      textInitPage,
      subTextInitPage,
      textUnderCards,
      formattedUnderCards,
      textListaVipSecond,
      textAccess,
      textDescount,
      textMemberFounder,
      textPrivacy,
      textDireitos,
      cards
    }
  }
})

</script>

<template>
  <q-layout view="hhh Lpr lFf">
    <q-header elevated class="bg-white header">
      <div class="header-content">
        <img src="/src/assets/Logo horizontal preta 4.png" alt="Logo FireBeauty" class="logo"
          style="width: 141px; height: 49px; margin-bottom: 10px;">
      </div>
    </q-header>

    <q-page-container class="page-container" style="padding-bottom: 0; background-color: #F3F3F3;">
      <q-page class="page-content">
        <div class="hero-section" style="position: relative; width: 100%;">
          <picture>
            <source media="(max-width: 768px)" srcset="/src/assets/img-mobile.png">
            <img src="/src/assets/Rectangle 3.png" alt="Background" class="hero-image">
          </picture>

          <div class="hero-content">
            <h1 class="hero-title">{{ titleText }}</h1>
            <p class="hero-subtitle">{{ subTitleText }}</p>

            <q-form class="form-card">
              <q-input outlined dense v-model="nome" class="form-input" label="Seu nome:" style="padding: 0;" />
              <q-input outlined dense v-model="whatsapp" label="Seu WhatsApp:" mask="(##) #####-####"
                class="form-input" />
              <q-btn label="Quero entrar na lista VIP!" class="form-button" />
            </q-form>

            <p class="form-disclaimer">
              <q-icon name="mdi-lock" color="#AD9B8E" size="16px" class="q-mr-xs" />
              {{ textListaVip }}
            </p>
          </div>
        </div>

        <!-- Main Content -->
        <div class="main-content">
          <div class="section-title">
            <p class="main-title">{{ textInitPage }}</p>
            <p class="sub-title" v-html="subTextInitPage"></p>
          </div>

          <div class="cards-container">
            <q-card class="info-card" v-for="(card, index) in cards" :key="index">
              <q-card-section class="card-content">
                <img :src="card.icon" alt="Ícone" class="card-icon">
                <div class="card-text">
                  <p class="card-title">{{ card.title }}</p>
                  <p class="card-description">{{ card.subtitle }}</p>
                </div>
              </q-card-section>
            </q-card>
          </div>

          <div class="under-cards-section">
            <div class="decorative-rectangle"></div>
            <p class="under-cards-text" v-html="formattedUnderCards"></p>
          </div>
        </div>

        <!-- VIP Section -->
        <div class="vip-section">
          <div class="vip-image mobile-first">
            <img src="/src/assets/lista-vip-img.png" alt="Lista VIP">
          </div>

          <div class="vip-content">
            <p class="vip-title">{{ textListaVipSecond }}</p>
            <ul class="vip-benefits">
              <li>{{ textAccess }}</li>
              <li>{{ textDescount }}</li>
              <li>{{ textMemberFounder }}</li>
            </ul>
            <q-btn class="vip-button" label="Reservar meu lugar com exclusividade" />
          </div>
        </div>

        <!-- Footer -->
        <q-footer class="page-footer" style="position: relative;">
          <div class="footer-content">
            <img src="/src/assets/Logo horizontal preta 4.png" alt="Logo FireBeauty" class="footer-logo">
            <p class="privacy-text">{{ textPrivacy }}</p>
          </div>
          <q-separator color="#D9D9D9" class="footer-separator" />
          <div style="justify-content: center; display: flex;">
            <p class="copyright-text">{{ textDireitos }}</p>
          </div>
        </q-footer>
      </q-page>
    </q-page-container>
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

/* Hero Section */
.hero-section {
  .hero-image {
    width: 100%;
    height: auto;
    object-fit: cover;

    @media (min-width: 769px) {
      height: 630px;
      /* 600px */
    }
  }

  .hero-content {
    position: absolute;
    top: 0;
    left: 5%;
    width: 90%;
    color: white;
    padding-top: 2.5rem;
    padding: 35px 20px;

    @media (min-width: 769px) {
      left: 8%;
      width: 37.5rem;
      /* 600px */
      padding-top: 5rem;
      /* 80px */
    }
  }

  .hero-title {
    font-family: 'IvyMode';
    font-size: 2.5rem;
    margin: 0;
    padding: 0 0 1.25rem 0;
    line-height: 1.2;
    white-space: pre-line;

    @media (min-width: 769px) {
      font-size: 4.375rem;
      padding: 0 0 40px 100px;
      line-height: 3.75rem;
    }
  }

  .hero-subtitle {
    font-family: 'Poppins';
    white-space: pre-line;
    font-weight: 400;
    line-height: 26px;
    font-size: 1rem;
    margin-left: 0;
    margin-bottom: 40px;
    width: 140px;
    color: $primary;

    @media (min-width: 769px) {
      margin-left: 100px;
      width: auto;
    }
  }

  .form-card {
    background-color: #D9D9D9;
    border-radius: 18px;
    font-family: 'Poppins';
    padding: 20px;

    @media (min-width: 769px) {
      margin: 1.75rem 0 0 6.25rem;
      padding: 20px;
    }
  }

  .form-input {
    background-color: #F5F5F5;
    border-radius: 8px;
    border: 2px solid #AD9B8E;
    margin-bottom: 16px;

    label {
      width: 30px;
    }
  }

  .form-button {
    background-color: #FFA600;
    color: #322D29;
    height: 2.8125rem;
    width: 100%;
    border-radius: 32.5px;
    font-weight: 600;
    font-size: 1rem;
    text-transform: none;

    @media (min-width: 769px) {
      width: 100%;
    }
  }

  .form-disclaimer {
    font-size: 1rem;
    display: flex;
    align-items: center;
    margin-top: 5px;
    margin-left: 0;
    color: $primary;

    @media (min-width: 769px) {
      margin-left: 100px;
      font-size: 0.8rem;
    }
  }
}

/* Main Content */
.main-content {
  padding: 32px 16px;

  @media (min-width: 769px) {
    padding: 64px 32px;
  }
}

.section-title {
  text-align: center;
  margin-bottom: 32px;

  .main-title {
    font-family: 'IvyMode';
    font-size: 2.5rem;
    color: $dark-brown;
    margin: 0;

    @media (min-width: 769px) {
      font-size: 4.375rem;
    }
  }

  .sub-title {
    font-family: 'Poppins';
    font-size: 1rem;
    color: $ligth-brown;
    margin-bottom: 16px;
    white-space: pre-line;

    @media (min-width: 769px) {
      margin-bottom: 34px;
      white-space: nowrap;
    }
  }
}

.cards-container {
  display: flex;
  flex-direction: column;
  gap: 16px;
  align-items: center;

  @media (min-width: 769px) {
    flex-direction: row;
    flex-wrap: wrap;
    justify-content: center;
    gap: 24px;
  }
}

.info-card {
  width: 202px;
  height: 194px;
  border: 3px solid transparent;
  border-radius: 16px;
  background: linear-gradient(white, #FFF6EF) padding-box,
    linear-gradient(45deg, #AD9B8E, #E9DFD7, #AD9B8E, #E9DFD7) border-box;
  box-shadow: 0 4px 10px rgba(0, 0, 0, 0.05);
  transition: transform 0.3s ease;

  &:hover {
    transform: translateY(-4px);
  }

  @media (min-width: 769px) {
    width: 212px;
    height: 204px;
  }

  .card-content {
    padding: 0;
    font-family: 'Poppins';
  }

  .card-icon {
    width: 2.5rem;
    margin: 6px;
  }

  .card-text {
    padding: 10px 30px;

    @media (min-width: 769px) {
      padding: 0 30px;
    }
  }

  .card-title {
    color: $dark-brown;
    font-size: 1.4rem;
    font-weight: 400;
    line-height: 15px;
    white-space: pre-line;
    margin: 0;
    padding-bottom: 0.3125rem;

    @media (min-width: 769px) {
      font-size: 1.2rem;
      font-weight: 400;
      line-height: 20px;
    }
  }

  .card-description {
    color: $tertiary;
    font-size: 1rem;
    line-height: 1.2rem;

    @media (min-width: 769px) {
      font-size: 0.7rem;
    }
  }
}

.under-cards-section {
  display: flex;
  align-items: center;
  justify-content: center;
  margin-top: 50px;

  @media (min-width: 769px) {
    margin-top: 90px;
  }

  .decorative-rectangle {
    width: 1.0625rem;
    height: 80px;
    background: $ligth-brown;
    margin-right: 0.75rem;
    flex-shrink: 0;

    @media (min-width: 769px) {
      height: 40px;
    }
  }

  .under-cards-text {
    font-family: 'Poppins';
    width: 190px;
    font-size: 1.25rem;
    font-weight: 600;
    color: $dark-brown;
    margin: 0;

    @media (min-width: 769px) {
      width: auto;
    }
  }
}

/* VIP Section */
.vip-section {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 2rem;
  margin-top: 2.5rem;
  padding: 0 1rem;

  @media (min-width: 769px) {
    flex-direction: row;
    justify-content: center;
    align-items: flex-start;
    gap: 54px;
    margin-bottom: 90px;
    padding: 0;
  }

  .vip-image {
    order: 1;
    width: 100%;
    max-width: 400px;

    @media (min-width: 769px) {
      order: 2;
    }
  }

  .vip-content {
    order: 2;
    width: 260px;
    max-width: 430px;
    margin-bottom: 50px;

    @media (min-width: 769px) {
      order: 1;
      width: auto;
    }
  }

  .vip-title {
    font-family: 'IvyMode';
    font-size: 2.45rem;
    font-weight: 600;
    color: $dark-brown;
  }

  .vip-benefits {
    font-family: 'Poppins';
    font-size: 1.1rem;
    color: $tertiary;
    padding-left: 20px;

    li {
      margin-bottom: 20px;
    }
  }

  .vip-button {
    font-family: 'Poppins';
    border-radius: 25.5px;
    background: linear-gradient(90deg, #CDBDB2 0%, #E9DFD7 100%);
    width: 260px;
    text-transform: none;
    font-weight: 600;
    line-height: 1.625rem;
    font-size: 1rem;
    color: $dark-brown;

    @media (min-width: 769px) {
      width: 380px;
    }
  }

  .vip-image {
    width: 100%;
    padding: 0 20px;

    @media (min-width: 769px) {
      padding: 0;
    }

    img {
      width: 100%;

      @media (min-width: 769px) {
        width: 450px;
      }
    }
  }
}

/* Footer */
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