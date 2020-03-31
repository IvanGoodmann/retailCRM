<template>
    <div id="app">
        <main>
            <div class="popup-box"
                 :class="{isOpen: popup}"
                 v-click-outside="closeForm"
            >
                <div class="popup-box__container">
                    <div class="form-box">
                        <div class="close-popup"
                             @click="closeForm"
                        >
                            <span></span>
                            <span></span>
                        </div>
                        <div class="form-box__title">
                            Заявка на карту
                        </div>
                        <form action="" method="post">
                            <validation-provider rules="required"
                                                 v-slot="{ errors }"
                                                 v-for="(item, i) in items"
                                                 :key="i"
                            >
                                <customInput
                                    :type="item.type"
                                    :name="item.model"
                                    :label="item.label"
                                ></customInput>
                                <span>{{ errors[0] }}</span>
                            </validation-provider>
                            <customSelect :selectLabel="selectLabel" :choices="countries"></customSelect>
                            <div class="form-check">
                                <input type="checkbox" class="form-check__input" id="checkPersonal"
                                       v-model="checkForm"
                                       @click="checkForm = !checkForm"
                                >
                                <label class="form-check__label" for="checkPersonal">
                                    Я соглашаюсь на <span

                                >
                                    обработку
                                </span>
                                    моих персональных данных
                                </label>
                            </div>
                            <div class="button-box">
                                <button type="submit" class="custom-button"
                                        :disabled="!checkForm"
                                >
                                    Заказать сейчас
                                </button>
                            </div>
                        </form>
                    </div>
                </div>
            </div>
            <div class="menu-box"
                 :class="{isOpen: isOpen}"
            >
                <div class="menu-box__item">
                    <div class="menu-box__item-link">Какие преимущества</div>
                    <div class="menu-box__item-link">Что вы получаете</div>
                    <div class="menu-box__item-link">Еще сюрпризы</div>
                    <div class="menu-box__item-link">Оформить карту</div>
                </div>
                <div class="menu-box__item">
                    <div class="menu-box__item-phone">
                        <span>По России</span>
                        8 800 950 6570
                    </div>
                    <div class="menu-box__item-phone">
                        <span>По Миру</span>
                        8 800 950 6570
                    </div>
                </div>
            </div>
            <header>
                <div class="container">
                    <div class="header-content">
                        <div class="burger-box"
                             @click.stop="toggle"
                             v-click-outside="close"
                             :class="{isOpen: isOpen}"
                        >
                            <div class="burger-box__item"></div>
                            <div class="burger-box__item"></div>
                            <div class="burger-box__item"></div>
                        </div>
                        <div class="logo-box">
                            <img src="@/assets/img/logo.png" alt="">
                        </div>
                    </div>
                </div>
            </header>
            <section class="block_01">
                <chart></chart>
                <div class="card-box obj">
                    <img src="@/assets/img/card.png" alt="">
                </div>
                <div class="container">
                    <div class="content">
                        <div class="title-box">
                            Твоя премиум
                            <div class="d-flex align-end">
                                карта <span>Лучшая карта для <b>любителей путешествий</b></span>
                            </div>
                        </div>
                        <div class="card-info">
                            <div class="card-info__item">
                                <div class="card-info__item-numb">
                                    11%
                                </div>
                                <div class="card-info__item-title">
                                    Вернем <br> за покупки <br> милями
                                </div>
                            </div>
                            <div class="card-info__item">
                                <div class="card-info__item-numb">
                                    0%
                                </div>
                                <div class="card-info__item-title">
                                    Бесплатное <br> снятие наличных <br> по всему миру
                                </div>
                            </div>
                            <div class="card-info__item">
                                <div class="card-info__item-numb">
                                    7%
                                </div>
                                <div class="card-info__item-title">
                                    До 7% <br> на остаток <br>по счету
                                </div>
                            </div>
                            <div class="card-info__item">
                                <div class="card-info__item-numb">
                                    0р
                                </div>
                                <div class="card-info__item-title">
                                    Бесплатное <br> годовое <br> обслуживание
                                </div>
                            </div>
                        </div>
                        <div class="button-box">
                            <button class="custom-button"
                                    @click.stop="openForm"
                            >
                                Заказать сейчас
                            </button>
                        </div>
                    </div>
                </div>
            </section>
            <section class="block_02">
                <div class="container">
                    <div class="content">
                        <div class="content-title">
                            Путешествие мечты начинается с CARD PLUS
                        </div>
                        <div class="content-subtitle">
                            Мы продумали каждую мелочь. Владельцы CARD PLUS получают особый <span>пакет привилегий, необходимый
                        для любого путешествия</span>
                        </div>
                        <div class="pluses-box">
                            <div class="pluses-box__item">
                                <div class="pluses-box__item-icon">
                                    <img src="@/assets/img/icon-plus_01.png" alt="">
                                </div>
                                <div class="pluses-box__item-title">
                                    Билеты любых авиакомпаний
                                </div>
                                <div class="pluses-box__item-description">
                                    Предложения от 300+ авиакомпаний, 185+ lowcost перевозчиков, чартеры от 60 крупных
                                    российских туроператоров
                                </div>
                            </div>
                            <div class="pluses-box__item">
                                <div class="pluses-box__item-icon">
                                    <img src="@/assets/img/icon-plus_02.png" alt="">
                                </div>
                                <div class="pluses-box__item-title">
                                    Мили больше не сгорают
                                </div>
                                <div class="pluses-box__item-description">
                                    Мили, накопленные при оплате картой AlfaTravel, не сгорают и остаются на вашем
                                    счете,
                                    пока вы не решите их потратить
                                </div>
                            </div>
                            <div class="pluses-box__item">
                                <div class="pluses-box__item-icon">
                                    <img src="@/assets/img/icon-plus_03.png" alt="">
                                </div>
                                <div class="pluses-box__item-title">
                                    Продвинутая страховка – бесплатно
                                </div>
                                <div class="pluses-box__item-description">
                                    Расширенная страховка для всей семьи с учетом экстремальных видов спорта и алкоголя
                                </div>
                            </div>
                            <div class="pluses-box__item">
                                <div class="pluses-box__item-icon">
                                    <img src="@/assets/img/icon-plus_04.png" alt="">
                                </div>
                                <div class="pluses-box__item-title">
                                    Доступ к счетам в разных валютах
                                </div>
                                <div class="pluses-box__item-description">
                                    Текущие счета в рублях, долларах США, евро, английских фунтах стерлингов и
                                    швейцарских
                                    франках открываются в любой момент
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
            </section>
            <section class="block_03">
                <div class="container">
                    <div class="content">
                        <div class="content-title">
                            Мы позаботились, чтобы вы получили
                        </div>
                        <div class="takes-box">
                            <div class="takes-box__item">
                                <div class="takes-box__item-image">
                                    <img src="@/assets/img/take-image_01.png" alt="">
                                </div>
                                <div class="takes-box__item-title">
                                    Бесплатный безлимитный интернет в роуминге
                                </div>
                                <div class="takes-box__item-icons">
                                    <img src="@/assets/img/take-icon_01.png" alt="">
                                    <img src="@/assets/img/take-icon_02.png" alt="">
                                    <img src="@/assets/img/take-icon_03.png" alt="">
                                    <img src="@/assets/img/take-icon_04.png" alt="">
                                </div>
                            </div>
                            <div class="takes-box__item">
                                <div class="takes-box__item-image">
                                    <img src="@/assets/img/take-image_02.png" alt="">
                                </div>
                                <div class="takes-box__item-title">
                                    Бесплатная упаковка багажа
                                </div>
                                <div class="takes-box__item-subtitle">
                                    Держатели карт Visa Signature могут упаковать багаж в крупных аэропортах России
                                </div>
                            </div>
                            <div class="takes-box__item">
                                <div class="takes-box__item-image">
                                    <img src="@/assets/img/take-image_03.png" alt="">
                                </div>
                                <div class="takes-box__item-title">
                                    Бесплатный доступ в приложении App In The Air
                                </div>
                                <div class="takes-box__item-subtitle">
                                    Бесплатная премиум подписка при покупке авиабилетов на travel.alfabank.ru
                                </div>
                            </div>
                            <div class="takes-box__item">
                                <div class="takes-box__item-image">
                                    <img src="@/assets/img/take-image_04.png" alt="">
                                </div>
                                <div class="takes-box__item-title">
                                    Такси бизнес-класса со скидкой 20%
                                </div>
                                <div class="takes-box__item-icons">
                                    <img src="@/assets/img/take-icon_05.png" alt="">
                                    <img src="@/assets/img/take-icon_06.png" alt="">
                                </div>
                            </div>
                            <div class="takes-box__item">
                                <div class="takes-box__item-image">
                                    <img src="@/assets/img/take-image_05.png" alt="">
                                </div>
                                <div class="takes-box__item-title">
                                    Скидка в ресторанах Novikov Group в аэропорту Шереметьево
                                </div>
                            </div>
                            <div class="takes-box__item">
                                <div class="takes-box__item-image">
                                    <img src="@/assets/img/take-image_06.png" alt="">
                                </div>
                                <div class="takes-box__item-title">
                                    Доступ в бизнес-залы Priority Pass по всему миру
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
            </section>
            <section class="block_04">
                <chart></chart>
                <div class="container">
                    <div class="content">
                        <div class="content-title">
                            Персональный помощник
                        </div>
                        <div class="content-freetitle">
                            Бесплатно для владельцев <span>CARD PLUS</span>
                        </div>
                        <div class="support-box">
                            <div class="support-box__item">
                                <div class="support-box__item-image">
                                    <img src="@/assets/img/girl.png" alt="">
                                </div>
                            </div>
                            <div class="support-box__item">
                                <div class="support-box__item-list">
                                    <div class="support-list__item">
                                        <div class="support-list__item-icon">
                                            <img src="@/assets/img/support-icon_01.png" alt="">
                                        </div>
                                        <div class="support-list__item-text">
                                            Организует встречи, найдет гидов и переводчиков
                                        </div>
                                    </div>
                                    <div class="support-list__item">
                                        <div class="support-list__item-icon">
                                            <img src="@/assets/img/support-icon_02.png" alt="">
                                        </div>
                                        <div class="support-list__item-text">
                                            Спланирует поездку по самым интересным местам вашего отдыха
                                        </div>
                                    </div>
                                    <div class="support-list__item">
                                        <div class="support-list__item-icon">
                                            <img src="@/assets/img/support-icon_03.png" alt="">
                                        </div>
                                        <div class="support-list__item-text">
                                            Достанет билеты на мероприятия, даже если их уже нет в продаже
                                        </div>
                                    </div>
                                    <div class="support-list__item">
                                        <div class="support-list__item-icon">
                                            <img src="@/assets/img/support-icon_04.png" alt="">
                                        </div>
                                        <div class="support-list__item-text">
                                            Закажет столик в ресторане, клубе или кафе
                                        </div>
                                    </div>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
            </section>
            <section class="block_05">
                <div class="container">
                    <div class="content">
                        <div class="content-title">
                            Оформите свою новую карту для путешествий
                        </div>
                        <div class="card-issue">
                            <div class="card-issue__item">
                                <div class="card-issue__item-numb">
                                    <span>до</span> 11%
                                </div>
                                <div class="card-issue__item-title">
                                    Милями за услуги, <br> оплаченные на travel.ru
                                </div>
                            </div>
                            <div class="card-issue__item">
                                <div class="card-issue__item-numb">
                                    <span>до</span> 11%
                                </div>
                                <div class="card-issue__item-title">
                                    Милями за любые <br> покупки по карте
                                </div>
                            </div>
                            <div class="card-issue__item">
                                <div class="card-issue__item-numb">
                                    1 = 1
                                </div>
                                <div class="card-issue__item-title">
                                    Оплата милями билетов любых <br> авиакомпаний по курсу 1 миля = 1 Р
                                </div>
                            </div>
                        </div>
                    </div>
                    <div class="order-info">
                        <div class="order-info__item">
                            <div class="order-info__item-image">
                                <img src="@/assets/img/card2.png" alt="">
                            </div>
                        </div>
                        <div class="order-info__item">
                            <div class="order-info__item-option">
                                <div class="option-tabs">
                                    <div class="option-tabs__item active">
                                        Кредитная карта
                                    </div>
                                    <div class="option-tabs__item">
                                        Дебетовая карта
                                    </div>
                                </div>
                                <div class="button-box">
                                    <button class="custom-button"
                                            @click.stop="openForm"
                                    >
                                        Заказать сейчас
                                    </button>
                                </div>
                                <div class="order-info__tab">
                                    <div class="order-info__tab-item">
                                        <div>Стоимость карты в год (руб.)</div>
                                        <div>
                                            <span>6 490 (без пакета услуг),</span>
                                            <span>4 990 (с пакетом услуг) </span>
                                        </div>
                                    </div>
                                    <div class="order-info__tab-item">
                                        <div>Приветственные мили (шт.)</div>
                                        <div>
                                            <span>1000</span>
                                        </div>
                                    </div>
                                    <div class="order-info__tab-item">
                                        <div>Стоимость карты в год (руб.)</div>
                                        <div>
                                            <span>5%</span>
                                        </div>
                                    </div>
                                </div>
                                <div class="more-info">
                                    <div class="more-info__title">
                                        Все подробности
                                    </div>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
            </section>
            <footer class="footer-box">
                <div class="obj chart-01">
                    <svg xmlns="http://www.w3.org/2000/svg" height="207" viewBox="0 0 1920 207" fill="none">
                        <path
                            d="M2007.34 201.528L1999.92 201.17L1974.57 197.004L1948.86 196.818L1923.75 192.009L1898.83 186.266L1872.93 186.605L1847.61 183.235L1823.64 173.244L1797.25 175.223L1771.85 172.347L1747.45 164.638L1723.37 159.811L1698.38 156.341L1679.62 139.504L1657.99 129.375L1633.07 124.261L1612.83 111.525L1592.02 99.6688L1569.32 90.7629L1549.68 76.691L1520.29 72.6936L1491.6 68.8489L1463.77 60.8542L1440.19 51.216L1422.26 34.7376L1401.26 22.204L1380.4 9.16483L1356.12 2.67743L1330.87 2L1306.6 9.2984L1282.51 13.923L1257.62 15.3803L1232.87 18.1732L1210.19 28.6246L1185.99 33.9911L1161.83 40.2924L1136.39 45.5395L1112.11 53.5677L1088.2 62.5952L1063.32 70.404L1036.26 70.3539L1016.83 54.0758L993.413 63.139L970.809 73.5189L947.179 82.0742L922.069 86.1288L897.34 88.0774L871.753 91.2256L846.738 83.3549L820.387 82.4009L794.609 78.9974L768.902 74.0532L744.389 77.1347L719.995 76.7292L695.815 80.0683L671.589 82.5249L646.669 81.5256L622.657 85.8784L597.929 85.6255L574.514 94.5004L549.619 89.9449L525.463 90.7224L501.05 93.2124L476.773 93.1958L454.394 82.6275L429.742 86.1836L406.384 89.0124L380.811 93.544L361.537 109.736L337.386 118.611L318.305 134.226L298.186 148.925L275.272 160.157L250.04 166.525L224.262 168.671L197.051 173.022L169.602 169.008L142.189 172.211L114.792 171.448L86.8773 171.142L63.1779 181.424L37.5689 183.659L11.8646 186.149L-10.6223 199.105L-35.9233 203.05L-48.5739 205.848"
                            stroke="#1E1E1E" stroke-width="2"/>
                    </svg>
                </div>
                <div class="container">
                    <div class="footer-content">
                        <div class="logo-box">
                            <img src="@/assets/img/logo.png" alt="">
                            <div class="logo-box__title">
                                АО «Кредит Европа Банк»
                            </div>
                        </div>
                        <div class="footer-menu">
                            <div class="footer-menu__item">
                                <div class="footer-menu__item-link">О банке</div>
                                <div class="footer-menu__item-link">Офисы и банкоматы</div>
                                <div class="footer-menu__item-link">Новости</div>
                                <div class="footer-menu__item-link">Вакансии</div>
                                <div class="footer-menu__item-link">Реализуемое имущество</div>
                            </div>
                            <div class="footer-menu__item">
                                <div class="footer-menu__item-link">Раскрытие информации</div>
                                <div class="footer-menu__item-link">Ставки по вкладам</div>
                                <div class="footer-menu__item-link">Условия и тарифы</div>
                                <div class="footer-menu__item-link">Корпоративное управление</div>
                                <div class="footer-menu__item-link">Карта сайта</div>
                            </div>
                        </div>
                        <div class="menu-box__item">
                            <div class="menu-box__item-phone">
                                <span>По России</span>
                                8 800 950 6570
                            </div>
                            <div class="menu-box__item-phone">
                                <span>По Миру</span>
                                8 800 950 6570
                            </div>
                        </div>
                    </div>
                </div>
            </footer>
        </main>
    </div>
</template>

<script>

  import ClickOutside from 'vue-click-outside'

  import Chart from './components/chart.vue'
  import customInput from './components/customInput.vue'
  import customSelect from './components/customSelect.vue'

  import { ValidationProvider, extend } from 'vee-validate';
  import { required } from 'vee-validate/dist/rules';

  extend('required', {
    ...required,
    message: 'This field is required'
  });

  export default {
    name: 'App',
    data: () => ({
      isOpen: false,
      popup: false,
      checkForm: false,
      selectLabel: 'Гражданство',
      value: '',
      email: '',
      name: '',
      phone: '',
      countries: [
        {
          label: 'Российская федерация',
          value: "RU"
        },
        {
          label: 'Белорусь',
          value: "BL"
        },
        {
          label: 'Украина',
          value: "UK"
        },
        {
          label: 'Казахстан',
          value: "KZ"
        },
      ],
      items: [
        {
          type: 'text',
          label: 'ФИО',
          model: 'name',
        },
        {
          type: 'email',
          label: 'Электронный адрес',
          model: 'email',
        },
        {
          type: 'text',
          label: 'Номер телефона',
          model: 'phone',
        }
      ]
    }),
    components: {
      Chart,
      customInput,
      customSelect,
      ValidationProvider
    },
    methods: {
      open() {
        this.isOpen = true;
      },
      close() {
        this.isOpen = false;
      },
      toggle() {
        this.isOpen ? this.close() : this.open();
      },
      openForm() {
        this.popup = true
      },
      closeForm() {
        this.popup = false
      },
    },
    directives: {
      ClickOutside
    },
    computed: {

    }
  }
</script>

<style lang="scss">
    @import './assets/scss/style.scss';
    @import './assets/scss/fonts.scss';
</style>
