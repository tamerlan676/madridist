<template lang="pug">
.game
  .hello-screen(v-if="firstScreen")
    .quest-count {{ questions.length }} вопросов
    h1 Тут вопрос по тесту на который вы должны ответить
    .game-desc Что делать, если у вас лихоманка или падучая? Проверьте, знаете ли вы, как в старину назывались болезни.
    button.button(@click="firstScreen = false, questionsScreen = true") Начать тест
  .questions(v-if="questionsScreen")
    .question(v-for="(item, id) in questions" :key="id" :class="{ show: item.show === true }") 
      .current {{ id+1 }} / {{ questions.length }}
      h3 {{ item.question }}
      img(:src="item.img")
      .variants-wrapper
        .variant(v-for="(variant, id) in item.variants" :key="id")
          .variant-inner(:class="callSomeClass(variant)")
            .variant-fields
              .input
                input(type="radio" :name="test" class="radio" :value="variant" @change="chooseVariant(variant)")
              label(:for="variant") {{ variant.title }}
            .variant-descr(:class="{showdesc: variant.selected === true}") {{ variant.descr}}
      button.button(@click="nextStep(id)" v-if="showBtn") Далее
  .lastScreen(v-if="lastScreen") 
    h1 Тест окончен
    p Правильных {{ correctAnswers }}  из {{ questions.length }}
</template>
    
  <script>
    export default{
      name: 'Game',
      layout: 'quiz',
      data() {
        return {
          firstScreen: true,
          lastScreen: false,
          inCorret: false,
          isCorrect: false,
          questionsScreen: false,
          correctAnswers: 0,
          showBtn: false,
          showClass: false,
          questions: [
            {
              question: 'Кто лучший игрок?',
              img: require('~/assets/images/hero.jpg'),
              show: true,
              variants: [
                {
                  title: 'Роналдо',
                  isCorrect: true,
                  selected: false,
                  descr: 'Конечно он'
                },
                {
                  title: 'Месси',
                  isCorrect: false,
                  selected: false,
                  descr: 'Гонишь?'
                },
                {
                  title: 'Z',
                  isCorrect: false,
                  selected: false,
                  descr: 'Конечно он'
                },
                {
                  title: 'A',
                  isCorrect: false,
                  selected: false,
                  descr: 'Гонишь?'
                }
              ]   
            },
            {
              question: 'Кто лучший боксер?',
              show: false,
              variants: [
                {
                  title: 'A',
                  isCorrect: true,
                  selected: false,
                  descr: 'Конечно он'
                },
                {
                  title: 'V',
                  isCorrect: false,
                  selected: false,
                  descr: 'Гонишь?'
                },
                {
                  title: 'C',
                  isCorrect: false,
                  selected: false,
                  descr: 'Конечно он'
                },
                {
                  title: 'C',
                  isCorrect: false,
                  selected: false,
                  descr: 'Гонишь?'
                }
              ]
            },
            {
              question: 'Кто лучший борец?',
              show: false,
              variants: [
                {
                  title: 'A',
                  isCorrect: false,
                  selected: false,
                  descr: 'Конечно он'
                },
                {
                  title: 'V',
                  isCorrect: false,
                  selected: false,
                  descr: 'Гонишь?'
                },
                {
                  title: 'C',
                  isCorrect: true,
                  selected: false,
                  descr: 'Конечно он'
                },
                {
                  title: 'C',
                  isCorrect: false,
                  selected: false,
                  descr: 'Гонишь?'
                }
              ]
            },
          ]
        }
      },
      methods: {
        nextStep(id) {
          if(id === this.questions.length - 1){
            this.questions[id].show = false
            this.lastScreen = true
            this.questionsScreen = false
          }
          else{
            this.questions[id].show = false
            this.questions[id+1].show = true
            this.showBtn = false
            this.showClass = false
            this.isCorret = false
          }
        },
        chooseVariant(variant){ 
          this.inCorret = true
          this.showBtn = true
          this.showClass = true
          variant.selected = true
          console.log(variant)
          if(variant.isCorrect){
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
    
<style lang="scss">
.game{
  height: 100vh;
  background: #000;
  display: flex;
  align-items: center;
  justify-content: center;
  .hello-screen, .questions, .lastScreen{
    width: 100%;
    background: #fff;
    padding: 40px 20px;
    .quest-count{
      width: fit-content;
      margin: 0 auto 20px;
    }
    h1{
      text-align: center;
      margin-bottom: 20px;
    }
    .game-desc{
      text-align: center;
      margin-bottom: 20px;
    }
  }
  .questions{
    .question{
      display: none;
      .current{
        width: fit-content;
        margin: 0 auto 20px;
      }
      h3{
        font-size: 24px;
        margin-bottom: 20px;
        text-align: center;
      }
      img{
        max-width: 100%;
      }
      &.show{
      display: block;
      }
    .variants-wrapper{
      margin-bottom: 20px;
    }
    .variant{
      border-bottom: 1px solid grey;
      .variant-fields{
        padding: 20px 0;
        display: flex;
        align-items: center;
        justify-content: center;
        .input{
          width: 36px;
          height: 36px;
          display: flex;
          align-items: center;
          input{
            width: 30px;
            height: 30px;
          }
        }
        .radio{
          width: 30px;
          margin-right: 8px;
        }
        label{
          width: 100%;
          cursor: pointer;
        }
      }
      .variant-inner{
        &.correct{
          background: rgb(139 197 139);
          position: relative;
          input{
            display: none;
          }
        }
        &.correct:before{
          position: absolute;
          content: '';
          width: 30px;
          height: 30px;
          background-image: url(~/assets/images/correct.svg);
          background-size: cover;
          background-position: center;
          top: 22px;
          left: 5px;
        }
        &.incorrect{
          background: rgb(235, 146, 146);
          position: relative;
          input{
            display: none;
          }
        }
        &.incorrect:before{
          position: absolute;
          content: '';
          width: 30px;
          height: 30px;
          background-image: url(~/assets/images/incorrect.svg);
          background-size: cover;
          background-position: center;
          top: 22px;
          left: 5px;
        }

      }
      .variant-descr{
        padding: 0 36px 10px 36px;
        font-style: italic;
        display: none;
        &.showdesc{
          display: block;
        }
      }
    }
  }
  }
  .button{
    width: 100%;
    display: flex;
    align-items: center;
    justify-content: center;
    padding: 20px;
    background: orange;
    color:#fff;
    font-weight: 800;
    text-transform: uppercase;
  }
}
</style>