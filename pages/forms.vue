//<img :src="`img/${item.logo}`"/>

<template lang="pug">
div
  center
    h1 TODO tel#mask, validation
  .body
    //p Оставьте сообщение которое сразу попадёт мне на телефон. 
    //p Если это важно, я оперативно отвечу.

    hr
    form(ref="about_form")
      .form
        input(type="text", name="entry.2078485491", placeholder="ваше Имя")
        input(type="text", name="entry.1577245810", placeholder="*  телефон или E-mail")
        textarea(name="entry.424724423", placeholder="Сообщение")
      button(disabled) Отправить
      //button(@click.prevent="submit()") Отправить

  //.btn(@click="show_rModal = true") Контакты
  // r-modal(:show.sync="showModal_4")
  // h1 Контакты 


</template>

<script>


//import rModal from '../components/ui/rModal';
//import Modal from '../components/ui/modal'


export default {
  components: {
    //rModal,
    //Modal,
  },
  data () {
    return {
      show_rModal: false,
    }
  },
  methods: {
    submit() {
      var form = this.$refs.about_form,
          btn = form.querySelector('button'),
          formData = new FormData(form);
      var req = new XMLHttpRequest();
      req.open('POST', 'https://docs.google.com/forms/d/e/1FAIpQLSfaJNL_ft-sWdWUDe_xUWmmnTqohjaFJNz7pVYSU95q9hH9iA/formResponse', true);
      req.send(formData);
      btn.classList.add('success');
      btn.innerHTML = 'Готово!';
      form.reset();
      setTimeout(function(){
        btn.classList.remove('success');
        btn.innerHTML = 'Отправить';
      }, 2000);
    }
    
  }
}
</script>

<style lang="styl">






</style>
