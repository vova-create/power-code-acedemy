<template>
  <div>
    <div>
      <select class="sign-form__select-lang" v-model="form.selectedCountry" @change="updatePhonePrefix">
        <option value="default">Выбирите страну</option>
        <option  value="ua">Ukraine</option>
        <option value="pl">Poland</option>
      </select>
    </div>
    <form @submit.prevent="submit" class="sign-form">
      <div class="sign-form__box">
        <div class="sign-form_header">
          <p>Запишитесь <span>бесплатно</span> <br/>и получите подарок</p>
        </div>
        <div class="sign-form__container">
          <input class="sign-form__input-field" type="text" id="name" v-model="form.name" placeholder="Ваше имя и фамилия">
          <div class="sign-form__errors">{{errors.name}}</div>
        </div>
        <div class="sign-form__container">
          <input class="sign-form__input-field" type="text" v-model="form.phone" placeholder="Ваш номер телефона">
          <div class="sign-form__errors">{{errors.phone}}</div>
        </div>
        <div class="sign-form__container">
          <input class="sign-form__input-field" type="text" id="email" v-model="form.email" placeholder="Ваш email">
          <div class="sign-form__errors">{{errors.email}}</div>
        </div>
        <button type="submit">Записаться бесплатно</button>
        <input class="test" type="checkbox" id="agreement">
        <label class="sign-form_agreement-text" for="agreement">Нажимая на кнопку я согашаюсь <br/>
        <u>с политикой конфидециальности</u> </label>
      </div>
    </form>
  </div>
</template>

<script>

const defaultForm = {
  name: '',
  email: '',
  selectedCountry: 'default',
  phone: '',
  isAgreed: false,
}
const defaultErrors = {
  name: '',
  phone: '',
  email:'',
}
export default {
  name: "SignForm",
  data() {
    return {
     form: {...defaultForm},
      errors: {...defaultErrors},
      canBeSent: false
    };
  },

  methods: {
    isValidEmail(email) {
      const emailRegex = /^\w+([.-]?\w+)*@\w+([.-]?\w+)*(\.\w{2,3})+$/;
      return emailRegex.test(email);
    },

    isValidPhoneNumber(phone) {
      const phoneRegex = /^\+[1-9]\d{1,14}$/;
      return phoneRegex.test(phone);
    },


    submit(){
      this.errors = {...defaultErrors}
      if (this.form.name.length < 3) {
        this.errors.name = 'Пожалуйста, введите ваше имя правильно';
      }
      if (!this.form.email) {
        this.errors.email = 'Пожалуйста, введите вашу почту';
      } else if (!this.isValidEmail(this.form.email)) {
        this.errors.email = 'Пожалуйста, введите вашу почту правильно';
      }

      if (!this.form.phone) {
        this.errors.phone = 'Пожалуйста, введите ваш номер';
      } else if (!this.isValidPhoneNumber(this.form.phone)) {
        this.errors.phone = 'Пожалуйста, введите ваш номер правильно';
      }

        if(this.errors['phone'] === '' && this.errors['name'] === '' && this.errors['email'] === ''){
          this.canBeSent = true
      }
      if(this.canBeSent) {
        const subject = 'Бесплатная запись';
        const body = `Name: ${this.form.name}\nEmail: ${this.form.email}\nPhone: ${this.form.phone}`;
        const mailtoUrl = `mailto:designer.web.studio.rgb@gmail.com?subject=${encodeURIComponent(subject)}&body=${encodeURIComponent(body)}`;
        window.location.href = mailtoUrl;
      }
    },
    updatePhonePrefix() {
      if (this.form.selectedCountry === 'ua') {
        this.form.phone = '+380';
      } else if (this.form.selectedCountry === 'pl') {
        this.form.phone = '+48';
      }
      else {
        this.phone = ''
      }
    }
  }
}
</script>

