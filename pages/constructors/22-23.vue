<template lang="pug">
.main
    .enter-name(v-if="step === 1") 
        .label Введите имя или фамилию на английском языке, которые нужно нанести на чехол.
        input(placeholder="ВВЕДИТЕ ИМЯ" v-model="name")
        .button.next(@click="step = 2", location.href="#") ДАЛЕЕ
    .enter-name(v-if="step === 2") 
        .label Введите номер, который нужно нанести на чехол.
        input(placeholder="ВВЕДИТЕ НОМЕР" v-model="number")
        button.next(@click="callMagic()") ДАЛЕЕ
    .magic(v-if="step === 3")
        .text Сейчас на ваших глазах происходит футбольная магия
        img.ball(src="~/assets/images/ball.svg")
    .final(v-if="step === 4") 
        .case-22-23 
            .name {{ name }}
            .number {{ number }}
        .buttons
            button.new(@click="step = 'options'") ЗАКАЗАТЬ
            button.new(@click="step = 1") ИЗМЕНИТЬ
    .options(v-if="step === 'options'") 
        .description
        .option
            h4 Выберите модель телефона
            select(v-model="model")
                option(disabled value="") Выберите один из вариантов
                option(v-for="(item, key) in getModels" :key="key") {{ item }}
            a.not-model(href="https://wa.me/79188208097" target="_blank") Моей модели нет в списке
        button.add-to-cart(@click="addToCart(product)" :class="{ active: model !== '' }") Добавить в корзину

</template>

<script>
export default{
    name: 'FootbolkaPage',
    data() {
    return {
        step: 1,
        name: '',
        number: '',
        model: '',
    }
    },
    head(){
        return {
          title: 'Чехол фаната Реал Мадрид',
          meta: [
            { hid: 'description', name: 'description', content: 'Заказать чехол Реал Мадрид можно на нашем сайте madridits.ru' },
          ]
    }
  },
    methods: {
    callMagic(){
        this.step = 3;
        setTimeout(() => {
        this.step = 4
        }, "2000")
    },
    addToCart(product) {
        this.$store.commit('addToCart', product)
        this.addedMessage = true
        setTimeout(() => {
        this.addedMessage = false
        }, 1500)
    },
    },
    computed: {
    getItem() {
        return this.$store.state.mobileCases.filter(item => item.id === +this.$route.params.id)[0]
    },
    getModels() {
        return this.$store.state.models
    },
    product() {
        return {
        title: 'Season 19-20',
        id: 123321,
        model: this.model,
        price: 1100,
        quantity: 1,
        image: require('~/assets/images/constructors/22-23.jpg'),
        shirtName: this.name,
        shirtNumber: this.number
        }
    }
    },
}  
</script>

<styles scoped lang="scss">
    .main{
    .title{
        width: 100%;
        padding: 16px;
        box-sizing: border-box;
        .xs{
        margin: 0 auto 24px;
        max-width: 100%;
        display: block;
        }
        .desc{
        text-align: center;
        font-weight: 500;
        font-size: 20px;
        margin-bottom: 24px;
        @media(min-width: 992px){
            width: 645px;
            margin: 0 auto 24px;
        }
        }
        .btn{
        background: #EF913A;
        width: 100%;
        height: 60px;
        color: #fff;
        font-size: 18px;
        display: flex;
        align-items: center;
        justify-content: center;
        font-weight: bold;
        letter-spacing: 5px;
        border-radius: 5px;
        @media(min-width: 768px){
            width: 300px;
            margin: 0 auto;
        }
        }
    }
    .enter-name{
        display: flex;
        flex-direction: column;
        justify-content: center;
        padding: 80px 16px;
        height: 80vh;
        @media(min-width: 992px){
            padding: 120px 0;
            margin: 0 auto;
            width: 500px;
        }
        .label{
        font-size: 20px;
        margin-bottom: 48px;
        text-align: center;
        font-weight: 500;
        }
        input{
            border: none;
            border-bottom: 4px solid #D9D9D9;
            width: 100%;
            height: 60px;
            text-align: center;
            font-weight: light;
            letter-spacing: 1.5px;
            font-size: 18px;
            outline: none;
            margin-bottom: 60px;
            text-transform: uppercase;
        }
        .next{
        background: var(--blue);
        width: 100%;
        height: 60px;
        color: #fff;
        font-size: 18px;
        display: flex;
        align-items: center;
        justify-content: center;
        font-weight: 500;
        letter-spacing: 5px;
        margin-bottom: 8px;
        @media(min-width: 768px){
            width: 300px;
            margin: 0 auto;
        }
        }
    }
    .magic{
        height: 80vh;
        display: flex;
        flex-direction: column;
        justify-content: center;
        padding: 16px;
        box-sizing: border-box;
        .text{
        text-align: center;
        font-size: 18px;
        }
        .ball{
        width: 100px;
        transform: rotate(45deg);
        margin: 20px auto;
        animation: zoom-rotate 5s linear infinite;
        // animation-direction: alternate;
        }
        @keyframes zoom-rotate {
        0% {
            transform: rotate(0deg);
        }
        100% {
            transform: rotate(360deg);
        }
        }
    }
    .final{
        padding: 16px;
        .case-22-23{
        width: 288px;
        height: 584px;
        background-image: url(~/assets/images/constructors/22-23-empty.jpg);
        margin: 30px auto 30px;
        position: relative;
        background-size: cover;
        .name{
            position: absolute;
            width: 100%;
            top: 180px;
            box-sizing: border-box;
            color: #000;
            text-align: center;
            text-transform: uppercase;
            font-size: 43px;
            font-family: '22-23';
            letter-spacing: 5px;
            margin: 0 auto;
        }
        .number{
            position: absolute;
            width: 100%;
            top: 235px;
            box-sizing: border-box;
            color: #000;
            text-align: center;
            text-transform: uppercase;
            font-size: 220px;
            font-family: '22-23';
            margin: 0 auto;
        }
        }
        .buttons{
            justify-content: space-between;
            margin: 0 auto;
            @media(min-width: 768px){
                display: flex;
                width: 700px;
            }
        }
        .new{
            background: var(--blue);
            width: 100%;
            height: 60px;
            color: #fff;
            font-size: 18px;
            display: flex;
            align-items: center;
            justify-content: center;
            font-weight: 500;
            letter-spacing: 5px;
            margin-bottom: 8px;
            @media(min-width: 768px){
                width: 300px;
                margin: 0 auto 20px;
            }
            }
    }
    .options{
        margin: 0 auto;
        padding: 16px;
        width: 100%;
        box-sizing: border-box;
        height: 80vh;
        display: flex;
        justify-content: center;
        flex-direction: column;
        @media(min-width: 768px){
            width: 500px;
            margin: 0 auto;
        }
    .option{
        margin-bottom: 32px;
        h4{
        margin-bottom: 10px;
        }
        select{
        width: 100%;
        font-size: 16px;
        padding: 5px;
        height: 45px;
        margin-bottom: 4px;
        border: 2px solid #000;
        color: #000;
        background: transparent;
        }
        .not-model{
        margin-bottom: 16px;
        display: block;
        }
        .custom-model{
        width: 100%;
        height: 40px;
        padding: 5px;
        font-size: 16px;
        box-sizing: border-box;
        border-radius: 5px;
        border: 2px solid #000;
        @media(min-width: 768px){
            width: 300px;
        }
        }
        .not-model{
        font-size: 13px;
        color: #6d6d6d
        }
        cursor: pointer;
        .colors{
        display: flex;
        align-items: center;
        .black{
            position: relative;
            width: 30px;
            height: 30px;
            border: none;
            background: transparent;
            margin-right: 12px;
            &:before{
            position: absolute;
            content: '';
            width: 30px;
            height: 30px;
            border-radius: 100%;
            top: -1px;
            left: -1px;
            background: rgb(44, 44, 44);
            cursor: pointer;
            border: 1px solid #e5e5e5
            }
            &:checked{
                &:before{
                border: 3px solid #67AAF9
                }
            }
            }
        .white{
            position: relative;
            width: 30px;
            height: 30px;
            border: none;
            background: transparent;
            &:before{
            position: absolute;
            content: '';
            width: 30px;
            height: 30px;
            border-radius: 100%;
            top: -1px;
            left: -1px;
            background: rgb(247, 247, 247);
            cursor: pointer;
            border: 1px solid #e5e5e5
            }
            &:checked{
                &:before{
                border: 3px solid #67AAF9
                }
            }
            }
        }
    }
    .description{
        margin-bottom: 24px;
    }
    }
    .add-to-cart{
        width: 100%;
        background: #e5e5e5;
        border-radius: 5px;
        padding: 15px;
        color: #fff;
        text-transform: uppercase;
        font-weight: 800;
        transition: .5s ease;
        margin-bottom: 24px;
        pointer-events: none;
        &.active{
            background: #005bff;
            pointer-events: all;
        }
    }
    .back-to-collection{
    display: block;
    margin: 0 auto;
    width: fit-content;
    color: #3468ac
    }
    }
</styles>