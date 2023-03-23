<template lang="pug">
.contacts
    h2 Наши контакты
    .text Вы можете связаться с нами любым удобным способом:
    .link(v-for="item in options")
        img(:src="item.img")
        a(:href="item.link" target="_blank") {{ item.text }}
    .divider
    h2 Самовывоз продукции
    .text Забрать чехол самостоятельно в городе Москва вы можете по адресу:
    .adresses-wrapper
    .adress
        .point-name г. Москва, Пресненская набережная 8
        .point-adress ТЦ "Афимолл"

</template>
    
    <script>
    export default{
      name: 'ContactUs',
      data() {
        return {
          map: 'https://yandex.ru/maps/?um=constructor%3A5fedb0800bc765bf95c201bc0b0dc85baba827dbed9932897fcc04e8377ed223&source=constructorLink',
          options: [
            {
              text: '+ 79188208097',
              img: require('~/assets/images/phone.svg'),
              link: 'tel:+79188208097'
            },
            {
              text: 'Написать в Telegram',
              img: require('~/assets/images/telegram.svg'),
              link: '#'
            },
            {
              text: 'Написать в WhatsApp',
              img: require('~/assets/images/whats.svg'),
              link: 'https://wa.me/79188208097'
            },
          ],
        }
      },
      head(){
            return {
              title: 'Контактная информация My Ossetia',
            }
      },
    }  
    </script>
    
    <style lang="scss">
    .contacts{
      padding: 16px;
      @media(min-width: 1200px){
        padding-top: 32px;
        min-height: 800px;
        width: 1120px;
        margin: 0 auto 92px;
      }
      h2{
        margin-bottom: 16px;
        @media(min-width: 1200px){
          margin-bottom: 32px;
        }
      }
      .text{
        margin-bottom: 24px;
      }
      .divider{
        height: 40px;
      }
      .link{
        display: flex;
        align-items: center;
        margin-bottom: 16px;
        img{
          width: 40px;
          margin-right: 10px;
        }
        a{
          color: rgb(71, 98, 139)
        }
      }
      .adresses-wrapper{
        display: flex;
        flex-direction: column;
        @media(min-width: 992px){
          flex-direction: row;
          flex-wrap: wrap;
          justify-content: space-between;
        }
        .adress{
          margin-bottom: 24px;
          background: rgb(246, 246, 246);
          padding: 15px;
          @media(min-width: 992px){
            width: 300px;
          }
          @media(min-width: 1200px){
            width: 46%;
          }
        .point-name{
          font-weight: 500;
          margin-bottom: 8px;
          font-size: 18px;
        }
        .point-adress{
          margin-bottom: 8px;
        }
        a{
          color: rgb(85, 118, 159)
        }
      }
      }
    }
    </style>