<template>
  <div class="header">
    <div class="icon">
      <img src="./assets/Star.png" style="width: 10%;">
      <p style="margin-left: 10px; font-weight: bold; color: var(--green); font-size: 20px;">Ink.House</p>
    </div>
    <div class="menu_bar">
      <p class="text menu hover">Репродукции</p>
      <p class="text menu hover">Новинки</p>
      <p class="text menu hover">О нас</p>
      <img class="icon_menu hover" src="./assets/Frame217.svg">
    </div>
  </div>
  <div class="first_screen">
    <img src="./assets/Layer 0 1.png" class="bird">
    <div class="info">
      <p class="text title">Реплики картин от <span style="color: var(--green) !important;">Ink. House</span></p>
      <p class="text description">Высокое качество отрисовки на плотной бумаге или льняном холсте. Редкие произведения, доступные цены.</p>
      <button class="butt">Продукция</button>
    </div>
  </div>
  <div class="reproductions">
    <div class="title_stroke">
      <p class="text main">Репродукции</p>
      <div class="country_bar">
        <div class="tab" @click="SelectCountry">
          <input type="radio" id="btn_fr" name="country" class="input_country" checked>
          <label for="btn_fr" class="butt country">Франция</label>
        </div>
        <div class="tab" @click="SelectCountry">
          <input type="radio" id="btn_ger" name="country" class="input_country">
          <label for="btn_ger" class="butt country">Германия</label>
        </div>
        <div class="tab" @click="SelectCountry">
          <input type="radio" id="btn_en" name="country" class="input_country">
          <label for="btn_en" class="butt country">Англия</label>
        </div>
      </div>
    </div>
    <div class="cards">
      <!-- v-for="element in elements.filter((x)=>x.SECTION_ID === section.ID)" -->
      <painting_card 
      v-for="elem in data.filter((x)=>x.country === selected_country)" 
      :key="elem" 
      :autor="elem.autor" 
      :material="elem.material" 
      :price="elem.price" 
      :name="elem.name" 
      :image="getImagePath(elem.image)"
      ></painting_card>
    </div>
  </div>
</template>

<script setup>
import {ref} from 'vue'
import painting_card from "./components/painting_card.vue" 

let selected_country = ref("Франция")



function SelectCountry (){
  let countries = document.querySelectorAll(".butt.country")
  let inputs = document.querySelectorAll(".input_country")

  for (let i = 0; i<countries.length; i++){
    if (inputs[i].checked){
      selected_country.value=countries[i].textContent
      break
    }
  }
}

const data = ref([
  {country: 'Франция', autor: 'Марсель Руссо', name: 'Охота Амура', material: 'Холст, масло (50х80) ', price: 14500 , image: 'f_6'},
  {country: 'Франция', autor: 'Анри Селин', name: 'Дама с собачкой', material: 'Акрил, бумага (50х80) ', price: 16500, image: 'f_1'},
  {country: 'Франция', autor: 'Франсуа Дюпон', name: 'Процедура', material: 'Цветная литография (40х60) ', price: 20000, image: 'f_2'},
  {country: 'Франция', autor: 'Луи Детуш', name: 'Роза', material: 'Бумага, акрил (50х80) ', price: 12000, image: 'f_3'},
  {country: 'Франция', autor: 'Франсуа Дюпон', name: 'Птичья трапеза', material: 'Цветная литография (40х60) ', price: 22500, image: 'f_4'},
  {country: 'Франция', autor: 'Пьер Моранж', name: 'Пейзаж с рыбой', material: 'Цветная литография (40х60) ', price: 20000, image: 'f_5'},
  {country: 'Германия', autor: 'Курт Вернер', name: 'Над городом', material: 'Цветная литография (40х60) ', price: 16000, image: 'g_6'},
  {country: 'Германия', autor: 'Макс Рихтер', name: 'Птенцы', material: 'Холст, масло (50х80) ', price: 14500, image: 'g_1'},
  {country: 'Германия', autor: 'Мартин Майер', name: 'Среди листьев', material: 'Цветная литография (40х60) ', price: 20000, image: 'g_2'},
  {country: 'Германия', autor: 'Герман Беккер', name: 'Яркая птица', material: 'Цветная литография (40х60) ', price: 13000, image: 'g_3'},
  {country: 'Германия', autor: 'Вульф Бауэр', name: 'Дятлы', material: 'Бумага, акрил (50х80) ', price: 20000, image: 'g_4'},
  {country: 'Германия', autor: 'Вальтер Хартманн', name: 'Большие воды', material: 'Бумага, акрил (50х80) ', price: 23000, image: 'g_5'},
  {country: 'Англия', autor: 'Пол Смит', name: 'Дикий зверь', material: 'Акварель, бумага (50х80) ', price: 19500, image: 'e_6'},
  {country: 'Англия', autor: 'Джон Уайт', name: 'Скалистый берег', material: 'Цветная литография (40х60) ', price: 17500, image: 'e_1'},
  {country: 'Англия', autor: 'Джим Уотсон', name: 'Река и горы', material: 'Акварель, бумага (50х80) ', price: 20500, image: 'e_2'},
  {country: 'Англия', autor: 'Юджин Зиллион', name: 'Белый попугай', material: 'Цветная литография (40х60) ', price: 15500, image: 'e_3'},
  {country: 'Англия', autor: 'Эрик Гиллман', name: 'Ночная рыба', material: 'Бумага, акрил (50х80) ', price: 12500, image: 'e_4'},
  {country: 'Англия', autor: 'Альфред Барр', name: 'Рыжий кот', material: 'Цветная литография (40х60) ', price: 21000, image: 'e_5'},
])

function getImagePath(imageFileName) {
  const images = require.context('@/assets/paintings/', false, /\.jpg$/);
  return images(`./${imageFileName}.jpg`);
}




</script>

<style>
.tab, .butt.country{
  display: inline-block;
}

.tab input[type="radio"] { 
  display: none; 
}


.tab :checked + .butt.country{
  background: var(--darkgreen);
  color: var(--white);
  display: block;
}

:root{
  --white: #F4F6F5;
  --gray: #86928B;
  --lightgreen: #E1EDE6;
  --green: #598D66;
  --darkgreen:#376B44;
  --black: #2C2D35;
  --lightyellow:#FAEB97;
  --yellow:#EEDB6D;
  --darkyellow:#D9B949;
}
body{
  margin: 0px;
  background: var(--white);
}
.header{
  position: fixed;
  background-color: var(--lightgreen);
  width: 100%;
  display: flex;
  align-items: center;
}
.icon{
  font-family: 'Raleway Bold';
  display: flex;
  align-items: center;
  margin: 0% 10% 0% 10%;
  width: 30%;
}
.menu{
  color: var(--black);
  font-size: 15px;
  margin: 20px;
  display: inline-block;
}
.menu_bar{
  display: flex;
  align-items: center;
  margin: 0% 5% 0% 5%;
  width: 40%;
}
.icon_menu{
  width: 15px;
  margin: 0% 5% 0% 5%;
}
.text{
  font-family: 'Raleway Light';
  color: var(--black);
  transition: 0.5s;
}
.hover:hover{
  text-shadow: black 0px 0px 10px;
  cursor: pointer;
  transition: 0.5s;
}
.bird{
  width: 50%;
}
.first_screen{
  padding: 10% 10% 0% 10%;
  display: flex;
  align-items: center;
}
.butt{
  font-size: 20px;
  font-family: 'Raleway Light';
  color: var(--green);
  background: none;
  border: solid 1px;
  padding: 10px 30px;
  margin-top: 40px;
  cursor: pointer;
  transition: 0.5s;
}
.butt:hover{
  transition: 0.5s;
  background: var(--green);
  color: var(--white);
}
.text.title{
  font-weight: bold;
  font-size: 40px;
}
.text.description{
  font-size: 15px;
  color: var(--gray);
}
.reproductions{
  padding: 0% 10% 0% 10%;
  margin-top: 100px;
}
.text.main{
  font-size: 25px;
  font-weight: bold;
  width: 50%;
}
.title_stroke{
  display: flex;
  align-items: center;
}
.butt.country{
  margin: 0px 10px;
  padding: 10px;
  border: none;
  background: var(--lightgreen);
  color: var(--black);
  border-radius: 50px;
  font-size: 15px;
  font-weight: bold;
}
.butt.country:hover{
  background: var(--darkgreen);
  color: var(--white);
}
.country_bar{
  width: 40%;
  margin: 0% 0% 0% 10%;
}
.cards{
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
}





@font-face {
	font-family: 'Raleway Light';
	src: url('./assets/fonts/Raleway_light/raleway_light.eot'); /* IE 9 Compatibility Mode */
	src: url('./assets/fonts/Raleway_light/raleway_light.eot?#iefix') format('embedded-opentype'), /* IE < 9 */
		url('./assets/fonts/Raleway_light/raleway_light.woff2') format('woff2'), /* Super Modern Browsers */
		url('./assets/fonts/Raleway_light/raleway_light.woff') format('woff'), /* Firefox >= 3.6, any other modern browser */
		url('./assets/fonts/Raleway_light/raleway_light.ttf') format('truetype'), /* Safari, Android, iOS */
		url('./assets/fonts/Raleway_light/raleway_light.svg#raleway_light') format('svg'); /* Chrome < 4, Legacy iOS */
}
@font-face {
	font-family: 'Raleway Bold';
	src: url('./assets/fonts/Raleway_bold/raleway_bold.eot'); /* IE 9 Compatibility Mode */
	src: url('./assets/fonts/Raleway_bold/raleway_bold.eot?#iefix') format('embedded-opentype'), /* IE < 9 */
		url('./assets/fonts/Raleway_bold/raleway_bold.woff2') format('woff2'), /* Super Modern Browsers */
		url('./assets/fonts/Raleway_bold/raleway_bold.woff') format('woff'), /* Firefox >= 3.6, any other modern browser */
		url('./assets/fonts/Raleway_bold/raleway_bold.ttf') format('truetype'), /* Safari, Android, iOS */
		url('./assets/fonts/Raleway_bold/raleway_bold.svg#raleway_bold') format('svg'); /* Chrome < 4, Legacy iOS */
}
</style>
