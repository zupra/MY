<template lang="pug">


div



  center
    h1 Элементы 

  h2 Expansion panel (Акордеон)
  h3 TODO модификаторы на #open
  expand(title='title expand')
    ol.textLi
      li Lorem ipsum dolor sit amet consectetur
      li Lorem ipsum dolor sit amet consectetur
      li Lorem ipsum dolor sit amet consectetur


  expand(title='title expand')
    h3 Lorem ipsum dolor sit amet
    p Lorem ipsum dolor sit amet consectetur, adipisicing elit. Blanditiis explicabo porro, voluptatum laborum cumque molestiae quibusdam accusamus sed, quam sint ducimus libero distinctio? Dolore laborum, quos dolorem recusandae deleniti quasi.


  hr




  p 
    i.tag .offsetBlock
  .offsetBlock
    h1 Модалки
    button(@click="showModal_1 = true") Show Modal(toCenter)
    button(@click="showModal_2 = true") Small Modal
    button(@click="showModal_3 = true") Large Modal
    button(@click="showModal_4 = true") Right Modal

  modal(:show.sync="showModal_1", size="toCenter", title='Lorem ipsum dolor sit amet')
    p Lorem ipsum dolor sit amet consectetur, adipisicing elit. Blanditiis explicabo porro, voluptatum laborum cumque molestiae quibusdam accusamus sed, quam sint ducimus libero distinctio? Dolore laborum, quos dolorem recusandae deleniti quasi.

  modal(:show.sync="showModal_2", size="SM")
    p  Заголовок не был назначен, поэтому только тело

  modal(:show.sync="showModal_3", size="XL", title='Окно для  «Широкого» контента')
    div(style="height: 420px;margin-top: 1rem")
      p.codepen(data-height='420', data-theme-id='0', data-slug-hash='BZLqGv', data-default-tab='result', data-user='dimaZubkov', data-embed-version='2', data-pen-title='Flexbox Overview')
        | See the Pen 
        a(href='https://codepen.io/dimaZubkov/pen/BZLqGv/') Flexbox Overview
        |  by Dima (
        a(href='https://codepen.io/dimaZubkov') @dimaZubkov
        | ) on 
        a(href='https://codepen.io') CodePen
        | .
      script(async='', src='https://production-assets.codepen.io/assets/embed/ei.js')

  r-modal(:show.sync="showModal_4")
    h1 Контакты 
    //Вопросы, предложения?
    .body
      p Оставьте сообщение которое сразу попадёт мне на телефон. 
      p Если это важно, я оперативно отвечу.
      hr
      form(ref="about_form")
        .form
          input(type="text", name="entry.2078485491", placeholder="ваше Имя")
          input(type="text", name="entry.1577245810", placeholder="*  телефон или E-mail")
          textarea(name="entry.424724423", placeholder="Сообщение")
        button Отправить
        //button(@click.prevent="submit()") Отправить


</template>


<script>

import Modal from '../components/ui/modal'
import rModal from '../components/ui/rModal'
import Expand from '../components/ui/expand'

//import tabs from '../components/ui/tabs'

export default {
  components: {
    Modal,
    rModal,
    Expand

  },
  data () {
    return {
      showModal_1: false,
      showModal_2: false,
      showModal_3: false,
      showModal_4: false
    }
  }
}
</script>