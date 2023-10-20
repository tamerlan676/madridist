<template lang="pug">
.questions
    h2.section-title Ответы на часто задаваемые вопросы
    .question-block(v-for="item in questions") 
        .question(@click=" item.open = !item.open") 
            .text {{ item.question }}
            .plus(:class="{ rotate: item.open === true }")
        .answer(:class="{ open: item.open === true }") {{ item.answer }}
</template>
            
            <script>
            export default {
                name: 'QuestionsAnswers',
                data() {
                    return {
                        questions: [
                            {
                                question: 'Вы делаете чехлы на любую модель телефонов?',
                                answer: 'Да, мы можем изготовить чехол как под айфоны, так и на любые телефоны с ОС Android',
                                open: false
                            },
                            {
                                question: 'Из чего сделаны ваши чехлы?',
                                answer: 'У нас есть 2 вида чехлов, из облегченного прорезиненного пластика и силиконовые. Печать на них держится долгое время.',
                                open: false
                            },
                            {
                                question: 'Есть ли у вас доставка? А самовывоз?',
                                answer: 'Мы можем отправить ваш чехол в любую точку мира, любым удобным способом. Забрать чехол самостоятельно можно из ТЦ Афимолл (г. Москва)',
                                open: false
                            },
                            {
                                question: 'Вы можете изготовить чехол с моим дизайном?',
                                answer: 'Запросто! Для этого нам от вас нужно изображение хорошего качества',
                                open: false
                            },
                            {
                                question: 'Как часто вы пополняете коллекцию?',
                                answer: 'Принты для чехлов изготавливают профессиональные дизайнеры. Мы стараемся пополнять нашу коллекцию раз в месяц',
                                open: false
                            },
                            {
                                question: 'Вы продаете только чехлы ?',
                                answer: 'На сегодняшний день да. Но мы планируем изготавливать разного рода сувениры в дальнейшем',
                                open: false
                            },
                        ]
                    }
                }
            
            }
            </script>
            
            <style lang="scss" scoped>
            .questions{
               padding: 40px 24px;
               @media(min-width: 1200px){
                    width: 1120px;
                    margin: 0 auto;
                    padding: 120px 0;
               }
               .section-title{
                margin-bottom: 24px;
               }
               .section-title::before{
                    position: absolute;
                    content: '';
                    width: 350px;
                    height: 8px;
                    bottom: 14px;
                    background: #FDDF55;
                    display: block;
                    z-index: -1;
                }
               .question-block{
                    border-bottom: 2px solid #000;
                    color: #000;
                    overflow: hidden;
                    position: relative;
                    .question{
                        display: flex;
                        align-items: center;
                        justify-content: space-between;
                        cursor: pointer;
                        height: 70px;
                        .text{
                            width: 300px;
                            @media(min-width:768px){
                                width: 100%;
                            }
                        }
                        .plus{
                            width: 35px;
                            height: 35px;
                            display: flex;
                            align-items: center;
                            justify-content: center;
                            font-size: 40px;
                            font-family: "Light";
                            background: #e5e5e5;
                            border-radius: 100%;
                            background: url(../assets/images/plus.svg);
                            background-size: cover;
                            transition: all .5s ease;
                            opacity: 0.5;
                            &.rotate{
                                transform: rotate(45deg);
                            }
                        }
                    }
               }
               .answer{
                    height: 0;
                    transition: all .5s ease;
                    color: #000;
                    &.open{
                        height: fit-content;
                        padding: 15px 0;
                    }
               }
            }
            
            </style>