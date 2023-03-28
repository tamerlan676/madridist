<template>
    <div class="main">
        <div v-if="currentStep === 1" class="quiz-block step-1">
          <div class="count-of-question">10 вопросов</div>
          <h1 class="main-question">Как хорошо вы знаете историю своего клуба?</h1>
          <p class="q-desc">Сейчас мы узнаем насколько вы преданный болельщик</p>
          <button @click="nextStep()" class="start">Начать Тест</button>
        </div>
          <div  class="quiz-block" v-if="currentStep === 2">
          <div class="count-of-question">1/10</div>
            <h2>{{ questions[0].question }}</h2>
            <img :src="questions[0].img" alt="">
            <div class="variants-wrapper">
              <div v-for="(v, id) in questions[0].variants" ref="variant" :class="callSomeClass(v)" :key="id"  class="variant">
                <div class="variant-inner">
                  <div class="input">
                    <input :id="id" type="radio" @change="chooseVariant(v)" :value="v" class="radio">
                  </div>
                  <label :for="id">{{ v.variant }}</label>
                </div>
                <div :class="{showdesc: v.selected === true}" class="descr">{{ v.descr }}</div>
              </div>
            </div>  
            <button v-if="showBtn" @click="nextStep()" type="reset" class="start">Следующий вопрос</button>
          </div>
          <div  class="quiz-block" v-if="currentStep === 3">
            <div class="count-of-question">2/10</div>
            <h2>{{ questions[1].question }}</h2>
            <img :src="questions[1].img" alt="">
            <div class="variants-wrapper">
              <div v-for="(v, id) in questions[1].variants" ref="variant" :class="callSomeClass(v)" :key="id"  class="variant">
                <div class="variant-inner">
                  <div class="input">
                    <input :id="id"  type="radio" @change="chooseVariant(v)" :value="v" class="radio">
                  </div>
                  <label :for="id">{{ v.variant }}</label>
                </div>
                <div :class="{showdesc: v.selected === true}" class="descr">{{ v.descr }}</div>
              </div>
            </div>  
            <button @click="nextStep()" v-if="showBtn" class="start">Следующий вопрос</button>
          </div>
          <div  class="quiz-block" v-if="currentStep === 4">
            <div class="count-of-question">3/10</div>
            <h2>{{ questions[2].question }}</h2>
            <div class="variants-wrapper">
              <div v-for="(v, id) in questions[2].variants" ref="variant" :class="callSomeClass(v)" :key="id"  class="variant">
                <div class="variant-inner">
                  <div class="input">
                    <input :id="id"  type="radio" @change="chooseVariant(v)" :value="v" class="radio">
                  </div>
                  <label :for="id">{{ v.variant }}</label>
                </div>
                <div :class="{showdesc: v.selected === true}" class="descr">{{ v.descr }}</div>
              </div>
            </div>  
            <button @click="nextStep()" v-if="showBtn" class="start">Следующий вопрос</button>
          </div>
          <div  class="quiz-block" v-if="currentStep === 5">
            <div class="count-of-question">4/10</div>
            <h2>{{ questions[3].question }}</h2>
            <div class="variants-wrapper">
              <div v-for="(v, id) in questions[3].variants" ref="variant" :class="callSomeClass(v)" :key="id"  class="variant">
                <div class="variant-inner">
                  <div class="input">
                    <input :id="id"  type="radio" @change="chooseVariant(v)" :value="v" class="radio">
                  </div>
                  <label :for="id">{{ v.variant }}</label>
                </div>
                <div :class="{showdesc: v.selected === true}" class="descr">{{ v.descr }}</div>
              </div>
            </div>  
            <button @click="nextStep()" v-if="showBtn" class="start">Следующий вопрос</button>
          </div>
          <div  class="quiz-block" v-if="currentStep === 6">
            <div class="count-of-question">5/10</div>
            <h2>{{ questions[4].question }}</h2>
            <div class="variants-wrapper">
              <div v-for="(v, id) in questions[4].variants" ref="variant" :class="callSomeClass(v)" :key="id"  class="variant">
                <div class="variant-inner">
                  <div class="input">
                    <input :id="id"  type="radio" @change="chooseVariant(v)" :value="v" class="radio">
                  </div>
                  <label :for="id">{{ v.variant }}</label>
                </div>
                <div :class="{showdesc: v.selected === true}" class="descr">{{ v.descr }}</div>
              </div>
            </div>  
            <button @click="nextStep()" v-if="showBtn" class="start">Следующий вопрос</button>
          </div>
          <div  class="quiz-block" v-if="currentStep === 7">
            <div class="count-of-question">6/10</div>
            <h2>{{ questions[5].question }}</h2>
            <div class="variants-wrapper">
              <div v-for="(v, id) in questions[5].variants" ref="variant" :class="callSomeClass(v)" :key="id"  class="variant">
                <div class="variant-inner">
                  <div class="input">
                    <input :id="id"  type="radio" @change="chooseVariant(v)" :value="v" class="radio">
                  </div>
                  <label :for="id">{{ v.variant }}</label>
                </div>
                <div :class="{showdesc: v.selected === true}" class="descr">{{ v.descr }}</div>
              </div>
            </div>  
            <button @click="nextStep()" v-if="showBtn" class="start">Следующий вопрос</button>
          </div>
          <div  class="quiz-block" v-if="currentStep === 8">
            <div class="count-of-question">7/10</div>
            <h2>{{ questions[6].question }}</h2>
            <div class="variants-wrapper">
              <div v-for="(v, id) in questions[6].variants" ref="variant" :class="callSomeClass(v)" :key="id"  class="variant">
                <div class="variant-inner">
                  <div class="input">
                    <input :id="id"  type="radio" @change="chooseVariant(v)" :value="v" class="radio">
                  </div>
                  <label :for="id">{{ v.variant }}</label>
                </div>
                <div :class="{showdesc: v.selected === true}" class="descr">{{ v.descr }}</div>
              </div>
            </div>  
            <button @click="nextStep()" v-if="showBtn" class="start">Следующий вопрос</button>
          </div>
          <div  class="quiz-block" v-if="currentStep === 9">
            <div class="count-of-question">8/10</div>
            <h2>{{ questions[7].question }}</h2>
            <div class="variants-wrapper">
              <div v-for="(v, id) in questions[7].variants" ref="variant" :class="callSomeClass(v)" :key="id"  class="variant">
                <div class="variant-inner">
                  <div class="input">
                    <input :id="id"  type="radio" @change="chooseVariant(v)" :value="v" class="radio">
                  </div>
                  <label :for="id">{{ v.variant }}</label>
                </div>
                <div :class="{showdesc: v.selected === true}" class="descr">{{ v.descr }}</div>
              </div>
            </div>  
            <button @click="nextStep()" v-if="showBtn" class="start">Следующий вопрос</button>
          </div>
          <div  class="quiz-block" v-if="currentStep === 10">
            <div class="count-of-question">9/10</div>
            <h2>{{ questions[8].question }}</h2>
            <div class="variants-wrapper">
              <div v-for="(v, id) in questions[8].variants" ref="variant" :class="callSomeClass(v)" :key="id"  class="variant">
                <div class="variant-inner">
                  <div class="input">
                    <input :id="id"  type="radio" @change="chooseVariant(v)" :value="v" class="radio">
                  </div>
                  <label :for="id">{{ v.variant }}</label>
                </div>
                <div :class="{showdesc: v.selected === true}" class="descr">{{ v.descr }}</div>
              </div>
            </div>  
            <button @click="nextStep()" v-if="showBtn" class="start">Следующий вопрос</button>
          </div>
          <div  class="quiz-block" v-if="currentStep === 11">
            <div class="count-of-question">10/10</div>
            <h2>{{ questions[9].question }}</h2>
            <div class="variants-wrapper">
              <div v-for="(v, id) in questions[9].variants" ref="variant" :class="callSomeClass(v)" :key="id"  class="variant">
                <div class="variant-inner">
                  <div class="input">
                    <input :id="id"  type="radio" @change="chooseVariant(v)" :value="v" class="radio">
                  </div>
                  <label :for="id">{{ v.variant }}</label>
                </div>
                <div :class="{showdesc: v.selected === true}" class="descr">{{ v.descr }}</div>
              </div>
            </div>  
            <button @click="nextStep()" v-if="showBtn" class="start">Узнать результат</button>
          </div>
          <div  class="quiz-block" v-if="currentStep === 12">
            <h2>Правильных ответов {{ correctAnswers }} из {{ questions.length }}</h2>
            <p  class="gift-text">Спасибо что прошел наш тест! <br> Мы дарим тебе промокод на скидку 20%</p>
            <div class="promocode">HALA20</div>
          </div>
    </div>
  </template>
  
  <script>
  export default {
    name: 'IndexPage',
    data() {
      return{
        showInfo: false,
        isCorrect: false,
        inCorret: false, 
        correctAnswers: 0,
        showClass: false,
        showBtn: false,
        currentStep: 12,
        questions: [
          {
            number: 1,
            question: 'Начнем с простого. Какой фрукт упоминают вспоминая о Мадридском Реале?',
            variants: [
              {
                variant: 'Слива',
                descr: 'Да! Реал по другому называют Сливочные',
                isCorrect: true,
                selected: false
              },
              {
                variant: 'Банан',
                descr: 'Соберись! Нужно быть повнимательнее',
                isCorrect: false,
                selected: false
              },
              {
                variant: 'Виноград',
                descr: 'Соберись! Нужно быть повнимательнее',
                isCorrect: false,
                selected: false
              },
              {
                variant: 'Ананас',
                descr: 'Соберись! Нужно быть повнимательнее',
                isCorrect: false,
                selected: false
              },
            ]
          },
                  {
            number: 2,
            question: 'Кто изображен на этом фото?',
            img: require('~/assets/images/hero.jpg'),
            variants: [
              {
                variant: 'Маноло Санчис',
                descr: 'Ты в лицо знаешь только Бензему похоже',
                isCorrect: false,
                selected: false
              },
              {
                variant: 'Фернандо Йерро',
                descr: 'Ты в лицо знаешь только Бензему похоже',
                isCorrect: false,
                selected: false
              },
              {
                variant: 'Альфредо Ди Стефано',
                descr: 'Верно! Это именно Альфредо. Но и другие парни - легенды',
                isCorrect: true,
                selected: false
              },
              {
                variant: 'Икер Касильяс',
                descr: 'Ты в лицо знаешь только Бензему похоже',
                isCorrect: false,
                selected: false
              },
            ]
          },
          {
            number: 3,
            question: 'Чей гол спас Реал от поражения в финале ЛЧ в 2014 году в игре против Атлетико',
            img: require('~/assets/images/hero.jpg'),
            variants: [
              {
                variant: 'Криштиано Роналдо',
                descr: 'Он, конечно забивал, но спас не он',
                isCorrect: false,
                selected: false
              },
              {
                variant: 'Серхио Рамос',
                descr: 'Именно! Это был волшебный гол с углового',
                isCorrect: true,
                selected: false
              },
              {
                variant: 'Лука Модрич',
                descr: 'Он не забил, но подал тот самый угловой',
                isCorrect: false,
                selected: false
              },
              {
                variant: 'Карим Бензема',
                descr: 'Ты в лицо знаешь только Бензему похоже',
                isCorrect: false,
                selected: false
              },
            ]
            },
            {
            number: 4,
            question: 'Кто из русских игроков играл за Реал Мадрид с 2009 по 2013 год?',
            img: require('~/assets/images/hero.jpg'),
            variants: [
              {
                variant: 'Андрей Аршавин',
                descr: 'Мимо! Андрей играл за Лондонский Асренал',
                isCorrect: false,
                selected: false
              },
              {
                variant: 'Федор Смолов',
                descr: 'Больше так не шути',
                isCorrect: false,
                selected: false
              },
              {
                variant: 'Денис Черышев',
                descr: 'Верно! Денис обладатель кубка ЛЧ в составе Реала',
                isCorrect: true,
                selected: false
              },
              {
                variant: 'Александр Головин',
                descr: 'Нет, но интересно было бы на это посмотреть',
                isCorrect: false,
                selected: false
              },
            ]
          },
          {
            number: 5,
            question: 'Сколько голов наколотил Криштиано Роналдо за Реал Мадрид?',
            img: require('~/assets/images/hero.jpg'),
            variants: [
              {
                variant: '330',
                descr: 'Холодно',
                isCorrect: false,
                selected: false
              },
              {
                variant: '400',
                descr: 'Холодно',
                isCorrect: false,
                selected: false
              },
              {
                variant: '450',
                descr: 'Верно! Уму не постижимо!',
                isCorrect: true,
                selected: false
              },
              {
                variant: '520',
                descr: 'Мимо, Соберись!',
                isCorrect: false,
                selected: false
              },
            ]
          },
          {
            number: 6,
            question: 'Кто из этих футболистов не играл за Мадридский Реал?',
            img: require('~/assets/images/hero.jpg'),
            variants: [
              {
                variant: 'Самуэль Этоо',
                descr: 'Этот парень играл за Реал',
                isCorrect: false,
                selected: false
              },
              {
                variant: 'Хавьер Савиола',
                descr: 'Этот парень играл за Реал',
                isCorrect: false,
                selected: false
              },
              {
                variant: 'Фабиньо',
                descr: 'Этот парень играл за Реал',
                isCorrect: false,
                selected: false
              },
              {
                variant: 'Фернандо Торрес',
                descr: 'Да! Фернандо прославился за другой Мадридский клуб',
                isCorrect: true,
                selected: false
              },
            ]
          },
          {
            number: 7,
            question: 'Какой тренер посадил на банку Икера Касильяса?',
            img: require('~/assets/images/hero.jpg'),
            variants: [
              {
                variant: 'Жозе Мауриньо',
                descr: 'Верно! Жозе предпочитал Диего Лопеса Икеру',
                isCorrect: true,
                selected: false
              },
              {
                variant: 'Фабио Капелло',
                descr: 'Не верно, соберись',
                isCorrect: false,
                selected: false
              },
              {
                variant: 'Зидан',
                descr: 'Не верно, соберись',
                isCorrect: false,
                selected: false
              },
              {
                variant: 'Карло Анчелотти',
                descr: 'Не верно, соберись',
                isCorrect: false,
                selected: false
              },
            ]
          },
          {
            number: 8,
            question: 'Какой тренер выиграл с Реалом 3 лиги чемпионов подряд?',
            img: require('~/assets/images/hero.jpg'),
            variants: [
              {
                variant: 'Зидан',
                descr: 'Верно! Зизу - легенда как игрок и как тренер',
                isCorrect: true,
                selected: false
              },
              {
                variant: 'Томас Тухель',
                descr: 'Его даже не было в Реале',
                isCorrect: false,
                selected: false
              },
              {
                variant: 'Гус Хиддинг',
                descr: 'Не верно, соберись',
                isCorrect: false,
                selected: false
              },
              {
                variant: 'Карло Анчелотти',
                descr: 'Карло пока еще этого не добился',
                isCorrect: false,
                selected: false
              },
            ]
          },
          {
            number: 9,
            question: 'Кого из этих игроков Реала тренировал Валерий Карпин',
            img: require('~/assets/images/hero.jpg'),
            variants: [
              {
                variant: 'Дениса Черышева',
                descr: 'Не верно',
                isCorrect: false,
                selected: false
              },
              {
                variant: 'Иско',
                descr: 'Не верно',
                isCorrect: false,
                selected: false
              },
              {
                variant: 'Макро Асенсио',
                descr: 'Верно! Марко играл в Мальорке, которую тренировал Карпин',
                isCorrect: true,
                selected: false
              },
              {
                variant: 'Андрей Лунин',
                descr: 'Не вено',
                isCorrect: false,
                selected: false
              },
            ]
          },
          {
            number: 10,
            question: 'Кто отдал голевую передачу в финале Лиги Чемпинов 2022 года ?',
            img: require('~/assets/images/hero.jpg'),
            variants: [
              {
                variant: 'Тони Кросс',
                descr: 'Этот парень много отдает, но в тот раз был не он',
                isCorrect: false,
                selected: false
              },
              {
                variant: 'Лука Модрич',
                descr: 'Этот парень много отдает, но в тот раз был не он',
                isCorrect: false,
                selected: false
              },
              {
                variant: 'Феде Вальверде',
                descr: 'Верно! Феде выдал тогда шикарный рывок с голевым пасом на Винисиуса',
                isCorrect: true,
                selected: false
              },
              {
                variant: 'Эден Азар',
                descr: 'Жаль, но это не он',
                isCorrect: false,
                selected: false
              },
            ]
          },
        ]
      }
    },
    methods: {
      nextStep(){
        const inputs = document.querySelectorAll('.radio');
        inputs.forEach(input => {
          input.checked = false;
        });
        this.currentStep++
        this.showInfo = false
        this.isCorrect = false
        this.inCorret = false 
        this.showClass = false
        this.showBtn = false
      },
      chooseVariant(val){ 
        this.inCorret = true
        this.showClass = true
        val.selected = true
        this.showBtn = true
        if(val.isCorrect){
          this.correctAnswers++
        }
      },
      callSomeClass(v){
        if(this.showClass){
          if(v.isCorrect){
            const className = 'correct' 
            return className
          }
          if(!v.inCorret && v.selected){
            return 'incorrect'
          }
        }
      }
    }
  }
  </script>
  
  <style>
  .main{
    width: 100%;
    height: 80vh;
    box-sizing: border-box;
    display: flex;
    align-items: center;
    justify-content: center;
    background: linear-gradient(-45deg, #ee7752, #972938, #23a6d5, #23d5ab);
    /* animation-name: 'color-change'; */
    animation-duration: 10s;
    animation-iteration-count: infinite;
    animation-delay: 2s;
  }
  .quiz-block{
    width: 100%;
    height: 100%;
    background-color: rgba(255, 255, 255, .8);
    padding: 16px;
    box-sizing: border-box;
    display: flex;
    align-items: center;
    flex-direction: column;
    justify-content: center;
  }
  .promocode{
    font-weight: bold;
    font-size: 24px;
    letter-spacing: 3px;
  }
  .quiz-block h2{
    margin-bottom: 16px;
    text-align: center;
  }
  .gift-text{
    text-align: center;
    margin-bottom: 20px;
  }
  .quiz-block img{
    max-width: 100%;
    margin-bottom: 20px;
  }
  .main-question{
    text-align: center;
    margin-bottom: 16px;
    font-size: 24px;
  }
  
  .q-desc{
    text-align: center;
    margin-bottom: 16px;
  }
  
  .start{
    background: orange;
    color: #fff;
    font-family: inherit;
    text-transform: uppercase;
    width: 100%;
    padding: 20px;
    border: none;
    cursor: pointer;
    font-size: 20px;
  }
  
  .variants-wrapper{
    width: 100%;
    margin-bottom: 20px;
  }
  .variant{
    width: 100%;
    border-bottom: 1px solid grey;
  }
  
  .variant-inner{
    display: flex;
    padding: 15px 5px;
    align-items: center;
  }
  
  .variant-inner .input{
    width: 36px;
  }
  
  .descr{
    display: none;
    padding: 0 36px 10px 36px;
  }
  .showdesc{
    display: block;
  }
  label{
    display: block;
    width: 100%;
    cursor: pointer;
    font-size: 18px;
  }
  .radio{
    margin-right: 8px;
    width: 30px;
  }
  .correct{
    background: rgb(139 197 139);
    position: relative;
  }
  .input{
    width: 36px;
    height: 36px;
    display: flex;
    align-items: center;
  }
  .correct input{
    display: none;
  }
  .correct:before{
    position: absolute;
    content: '';
    width: 30px;
    height: 30px;
    background-image: url(~/assets/images/correct.svg);
    background-size: cover;
    background-position: center;
    top: 18px;
    left: 5px;
  }
  .incorrect{
    background: rgb(235, 146, 146);
    position: relative;
  }
  .incorrect:before{
    position: absolute;
    content: '';
    width: 30px;
    height: 30px;
    background-image: url(~/assets/images/incorrect.svg);
    background-size: cover;
    background-position: center;
    top: 18px;
    left: 5px;
  }
  .incorrect input{
    display: none;
  }
  @media (min-width : 768px) {
    .main{
      padding: 32px;
    }
  }
  @media (min-width : 992px) {
  .quiz-block{
    width: 530px;
    min-height: 500px;
   }
  }
  @media (min-width : 1200px) {
  .quiz-block{
    width: 630px;
    height: fit-content;
   }
  }
  </style>
  