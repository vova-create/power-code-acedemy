<template>
<div class="info-block">
    <div class="info-block__button-shape-info">
      <img class="info-block__icon" src="@/assets/icons/earth-net.png" height="19" width="19"/>
      Вебинар
    </div>
    <div>
      <div class="info-block__main-title">front-end</div>
      <p class="info-block__main-sub-title">
        <span class="info-block__from-zero">с нуля</span>
        легкий старт в IT профессии
      </p>
      <p class="info-block__main-text">Узнайте какими навыками должен обладать фронтенд разработчик в 2022 году и как начать карьеру в востребованной профессии <br/>
       <span class="info-block__with-salary">с зарплатой</span>  <span class="info-block__from-thousand">от 1 000$</span></p>
    </div>
  <SignForm class="sign-form__show-mobile"/>
  <div class="info-block__details">
      <div class="info-block__details-item">
        <img src="@/assets/icons/man-and-laptop.png" height="44" width="37"/>
        <div class="info-block__details-text">
          <p class="info-block__details-name">Кирилл <span class="info-block__details-family-name">КАСАТОНОВ</span></p>
          <p class="info-block__details-text-descriptions">6 лет коммерческого опыта с такими  компаниями как <br/> Mercedes-Benz и другими крупными корпорациями</p>
        </div>
      </div>
      <div class="info-block__details-item">
        <img src="@/assets/icons/gift.png" height="39" width="38"/>
        <div class="info-block__details-text">
          <p class="info-block__details-name">Бонус за регистрацию</p>
          <p class="info-block__details-text-descriptions">PDF-файл "5 преимуществ <br> профессии фронтенд разработчика" </p>
        </div>
      </div>
    </div>
</div>
</template>

<script>
import SignForm from "@/components/SignForm.vue";
export default {
  name: "InfoBlock",
  components:{
    SignForm

  }

}
</script>


