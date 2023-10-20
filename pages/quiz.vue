<template>
    <div class="main">
        <div v-if="currentStep === 1" class="quiz-block step-1">
          <div class="count-of-question">10 вопросов</div>
          <h1 class="main-question">Проверь как хорошо ты знаешь Джуда Беллингема?</h1>
          <p class="q-desc">Сейчас мы узнаем насколько ты преданный фанат</p>
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
            <p  class="gift-text">Спасибо что прошел наш тест! <br> Поделись результатом в группе</p>
            <!-- <div class="promocode">HALA20</div> -->
            <button class="start" @click="reload">ПОДЕЛИТЬСЯ</button>
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
        currentStep: 1,
        questions: [
          {
            number: 1,
            question: 'Начнем с простого. Под каким номер Джуд выступает за мадридский Реал?',
            variants: [
              {
                variant: '5',
                descr: 'Да! Его уже все сравнивают с легендарным Зизу',
                isCorrect: true,
                selected: false
              },
              {
                variant: '7',
                descr: 'Соберись! Нужно быть повнимательнее',
                isCorrect: false,
                selected: false
              },
              {
                variant: '22',
                descr: 'Соберись! Нужно быть повнимательнее',
                isCorrect: false,
                selected: false
              },
              {
                variant: '17',
                descr: 'Соберись! Нужно быть повнимательнее',
                isCorrect: false,
                selected: false
              },
            ]
          },
                  {
            number: 2,
            question: 'Какой игрок является кумиром для Джуда?',
            variants: [
              {
                variant: 'Зидан',
                descr: 'Не верно. Его с ним только сравнивают',
                isCorrect: false,
                selected: false
              },
              {
                variant: 'Месси',
                descr: 'Ходил такой слух, но это не правда',
                isCorrect: false,
                selected: false
              },
              {
                variant: 'Джеррард',
                descr: 'Верно! Джуд восхищался им все детство',
                isCorrect: true,
                selected: false
              },
              {
                variant: 'Мбаппе',
                descr: 'Не верно. Может наоборот, Джуд его кумир',
                isCorrect: false,
                selected: false
              },
            ]
          },
          {
            number: 3,
            question: 'Как добирался Джуд на тренировки первое время, когда только перешел в Реал?',
            variants: [
              {
                variant: 'На метро',
                descr: 'Нет уж, это слишком',
                isCorrect: false,
                selected: false
              },
              {
                variant: 'Возила мама',
                descr: 'Именно! Это безумно мило',
                isCorrect: true,
                selected: false
              },
              {
                variant: 'Пешком',
                descr: 'Ты чего! Это долго',
                isCorrect: false,
                selected: false
              },
              {
                variant: 'На вертолете',
                descr: 'Не верно. Но может в будущем такое возможно',
                isCorrect: false,
                selected: false
              },
            ]
            },
            {
            number: 4,
            question: 'А ты знаешь как зовут родного брата Джуда?',
            variants: [
              {
                variant: 'Стив',
                descr: 'Мимо!',
                isCorrect: false,
                selected: false
              },
              {
                variant: 'Федор',
                descr: 'Больше так не шути',
                isCorrect: false,
                selected: false
              },
              {
                variant: 'Джоб',
                descr: 'Верно! Родители особо не фантаизируют',
                isCorrect: true,
                selected: false
              },
              {
                variant: 'Месроп',
                descr: 'Нет, но интересно было бы на это посмотреть',
                isCorrect: false,
                selected: false
              },
            ]
          },
          {
            number: 5,
            question: 'Какую сумму Реал официально заплатил за Джуда?',
            variants: [
              {
                variant: '50 млн евро',
                descr: 'Холодно',
                isCorrect: false,
                selected: false
              },
              {
                variant: '200 млн евро',
                descr: 'Холодно',
                isCorrect: false,
                selected: false
              },
              {
                variant: '130 млн евро',
                descr: 'Верно!',
                isCorrect: true,
                selected: false
              },
              {
                variant: 'Так он же бесплатно пришел',
                descr: 'Хотелось бы конечно, но нет',
                isCorrect: false,
                selected: false
              },
            ]
          },
          {
            number: 6,
            question: 'В каком футбольном клубе Джуд дебютировал в 16 лет?',
            variants: [
              {
                variant: 'Сток сити',
                descr: 'Не попал',
                isCorrect: false,
                selected: false
              },
              {
                variant: 'Манчестер Сити',
                descr: 'Мимо',
                isCorrect: false,
                selected: false
              },
              {
                variant: 'Болтон',
                descr: 'Этот парень не играл за Болтон',
                isCorrect: false,
                selected: false
              },
              {
                variant: 'Бирмингем',
                descr: 'Да! Фанаты до сих пор обажают Джуда',
                isCorrect: true,
                selected: false
              },
            ]
          },
          {
            number: 7,
            question: 'Какой тренер 3 часа уговаривал Джуда перейти в его клуб, а не в Реал Мадрид?',
            variants: [
              {
                variant: 'Пеп Гвардиола',
                descr: 'Верно! Пеп очень хотел Джуда в Сити',
                isCorrect: true,
                selected: false
              },
              {
                variant: 'Юрген Клопп',
                descr: 'Не верно, соберись',
                isCorrect: false,
                selected: false
              },
              {
                variant: 'Сергей Семак',
                descr: 'Этому бы и 3 лет не хватило на это',
                isCorrect: false,
                selected: false
              },
              {
                variant: 'Карло Анчелотти',
                descr: 'Даже уговаривать не пришлось',
                isCorrect: false,
                selected: false
              },
            ]
          },
          {
            number: 8,
            question: 'В каком году Джуд сыграл свой дебютный матч в Лиге Чемпионов?',
            variants: [
              {
                variant: '2020',
                descr: 'Верно! Ему на тот момент было 17 лет и 117 дней',
                isCorrect: true,
                selected: false
              },
              {
                variant: '2021',
                descr: 'Не верно',
                isCorrect: false,
                selected: false
              },
              {
                variant: '2022',
                descr: 'Не верно, соберись',
                isCorrect: false,
                selected: false
              },
              {
                variant: '2023',
                descr: 'К этому времени он уже даже забил несколько голов',
                isCorrect: false,
                selected: false
              },
            ]
          },
          {
            number: 9,
            question: 'Какому клубу Джуд забил свой первый гол в Лиге Чемпионов?',
            variants: [
              {
                variant: 'Байер',
                descr: 'Не верно',
                isCorrect: false,
                selected: false
              },
              {
                variant: 'Реал Сосьедад',
                descr: 'Не верно',
                isCorrect: false,
                selected: false
              },
              {
                variant: 'Манчестер Сити',
                descr: 'Верно! Гвардило уже тогда начал охоту на Джуда',
                isCorrect: true,
                selected: false
              },
              {
                variant: 'ЦСКА',
                descr: 'Не верно',
                isCorrect: false,
                selected: false
              },
            ]
          },
          {
            number: 10,
            question: 'Какому клубу Джуд забил свой первый гол в Ла Лиге ?',
            variants: [
              {
                variant: 'Бетис',
                descr: 'Не верно',
                isCorrect: false,
                selected: false
              },
              {
                variant: 'Атлетико',
                descr: 'Им еще не забил',
                isCorrect: false,
                selected: false
              },
              {
                variant: 'Атлетик',
                descr: 'Верно! Усепшный дебют для Джуда привел Реал к победе',
                isCorrect: true,
                selected: false
              },
              {
                variant: 'Барселона',
                descr: 'Ждем и этого, но пока нет',
                isCorrect: false,
                selected: false
              },
            ]
          },
        ]
      }
    },
    methods: {
        reload(){
            location.href="https://vk.com/madridistru"
        },
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
  
  <style scoped>
  .main{
    width: 100%;
    min-height: 80vh;
    box-sizing: border-box;
    display: flex;
    align-items: center;
    justify-content: center;
    background: linear-gradient(-45deg, #2a0978, #254bc9, #23a6d5, #1083aa);
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
    margin-bottom: 24px;
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
  